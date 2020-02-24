**I have 12+ micro services to be migrated from python2.X and I will be listing complete details of porting issues whatever is not listed in the below and how to address them as well with examples, Keep watching this section**


## python-2-To-3 
Tips  for Migrating Python 2.7.x to  3.x  from python community
* cheat sheet - http://python-future.org/compatible_idioms.html
* porting 2 to 3 - https://docs.python.org/3/howto/pyporting.html
* Majority of the problems is due to the Text v/s binary data returned by functions more details for better understanding: https://blog.feabhas.com/2019/02/python-3-unicode-and-byte-strings/


## Here are some snippets for yo to focus on while migrating

```python

class SomeClassWithoutBaseClass:                    ==> class SomeClassWithoutBaseClass(object):

base_product.validate = lambda (payload): payload  	==>  base_product.validate = lambda payload : payload
event = {k: to_str(v) for k, v in event.items()}  	==> event = {k: to_str(v) for k, v in list(event.items())}
for key, value in upstream_catalog.iteritems():			==>   for key, value in upstream_catalog.items():
        merged_catalog.setdefault(key, value)										merged_catalog.setdefault(key, value)

VOUCHER_PATTERN = '[\d\l]{{{length}}}'              ==>   VOUCHER_PATTERN = r'[\d\l]{{{length}}}'

map(lambda item: item.someFunc(), results)  				==> 		list(map(lambda item: item.someFunc(), results))


cashed = int(round((float(cash) / tot_amt) * 100))  		==> cashed = int(round((float(cash) // tot_amt) * 100))


for keytuple in purchases_products.keys():   				==>  for keytuple in list(purchases_products.keys():


return products_by_id.values()    									==> return list(products_by_id.values())


return unicode(self.template).format(**self.kwargs) 		==> return str(self.template).format(**self.kwargs)


try:
    # py3 moved to collections package
    from collections import UserDict        # noqa
except ImportError:
    from UserDict import UserDict           # noqa
    

```

