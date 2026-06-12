---
title: "working with iteritems() for dictionary:python"
date: 2012-05-04
forum: General Help
---

### Post by nischalinn on 2012-05-04
I've got strange error with iteritems(). why is it so?
```
>>> class test:
	def __init__(self,**marks):
		self._marks = marks
	def getMarks(self):
		for key,value in self._marks.iteritems():
			print (self._marks(key,value))

			
>>> t1=test(sub1=99,sub2=98)
>>> t1.getMarks()
Traceback (most recent call last):
  File "<pyshell#12>", line 1, in <module>
    t1.getMarks()
  File "<pyshell#10>", line 5, in getMarks
    for key,value in self._marks.iteritems():
**AttributeError: 'dict' object has no attribute 'iteritems'**
```

but when i did items(), it works well

```
__dict = {'sub1':99,'sub2':98}

>>> for key,val in __dict.items():
	print(key,val)

	
sub2 98
sub1 99
```

Also i need to print the result in the same order as in the input i.e.
[B]sub1 99 
sub2 98. [/B]
how can I do it?
**********************
I would like to generate a error message when someone enters a duplicate items.
marks1 = marks(sub1 = 99, sub2 = 98, sub3 = 99)
when again 99 is re-entered it generates an error message. how can I do it?
__________________

---

### Post by PeterP24 on 2012-05-04
If you want to control the order of the items in your dictionary you can use OrderedDict from collections module.

---

