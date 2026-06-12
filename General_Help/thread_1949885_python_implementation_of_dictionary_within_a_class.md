---
title: "python: implementation of dictionary within a class"
date: 2012-03-31
forum: General Help
---

### Post by nischalinn on 2012-03-31
I want to design:
1. address class ->using dictionary data structure where items are; state, city and street for individual person
2. name class -> person's first and last name
3. display class -> searches for the given name and displays the address of that particular name

my questions are:
1. how to design the address class such that it takes name of the person from the name class and stores the address info. in a dictionary?
2. how to make search for the name and display of the address information?

---

### Post by nischalinn on 2012-04-02
```

class name:
	def __init__(self, firstName, lastName):
		self.firstName = firstName
		self.lastName = lastName
		
class address(name):
	def __init__(self):
		super.__init__(firstName, lastName)
		self.completeAddress = {
			"state": self.state,
			"city": self.city,
			"street": self.street
		}
		
class search:
	print("enter the firstname or lastname or complete name seperated by space of the person: ")

```

My problems are now:

1. if the user enters the firstName, it should return all the address related to the firstName
2. if the user enters the lastName, it should return all the address related to that lastName
3. if the user enters completeName, the search class should take both firstName and lastName and give the result, is it possible?

I need another class to display the result.
How can I solve this, I can't proceed further.

---

