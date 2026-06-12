---
title: "python: problem implementing class, inheritance, overriding"
date: 2012-03-31
forum: General Help
---

### Post by nischalinn on 2012-03-31
```

class contactList(list):
'''Return all contacts that contain the search value in their name.'''
	def search(self,name):
		matchingContact = []
		for contact in self:
			if name in contact.name:
				mathcingContact.append(contact)
			
class contact:
	allContact = contactList()
	def __init__(self, name, email):
		self.name = name 
		self.email = email
		self.allContact.append(self)
		
class supplier(contact):
	def __init__(self,order):
		print("for supplier" "{} order to {}".format(order,self.name))
		
class friend(contact):
	def __init__(self,name, email, phone):
		super().__init__(name,email)
		self.phone = phone

```
> 
>>> from contacts import contactList, contact,supplier,friend
Traceback (most recent call last):
  File "<pyshell#26>", line 1, in <module>
    from contacts import contactList, contact,supplier,friend
ImportError: cannot import name contactList
>>> from contacts import contact,supplier, friend
Traceback (most recent call last):
  File "<pyshell#27>", line 1, in <module>
    from contacts import contact,supplier, friend
ImportError: cannot import name friend


why can't I import contactList and friend??

> 
>>> s1 = supplier("sss", "sss@gmail.com")
Traceback (most recent call last):
  File "<pyshell#31>", line 1, in <module>
    s1 = supplier("sss", "sss@gmail.com")
TypeError: __init__() takes exactly 2 positional arguments (3 given)


why is this error showing though I've inherited the class **contact**???

> 
>>> f1 = friend("fff" , "fff@gmail.com", "123")
Traceback (most recent call last):
  File "<pyshell#34>", line 1, in <module>
    f1 = friend("fff" , "fff@gmail.com", "123")
NameError: name 'friend' is not defined

why is this error showing??

> 
>>> c2 = contact("ccc" , "ccc@")
>>> c3 = contact("ccc1" , "cc@@")
>>> c4 = contact("cccc", "ccc@@@")
>>> [c.name for c in contact.allContact.search('ccc')]
Traceback (most recent call last):
  File "<pyshell#38>", line 1, in <module>
    [c.name for c in contact.allContact.search('ccc')]
AttributeError: type object 'contact' has no attribute 'allContact'


And what is this??

I've taken this example from **python3 object oriented programming**.

---

