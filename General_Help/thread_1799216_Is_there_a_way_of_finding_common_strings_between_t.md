---
title: "Is there a way of finding common strings between two files?"
date: 2011-07-07
forum: General Help
---

### Post by sirverdemer on 2011-07-07
Hi!
I have two text files in the form:

1 ItemA [value]
2 ItemB [value]
3 ItemC [value]

Some of these items are common for both files, while others are missing from either one or the other. 
I want to compare the values for each common item in the two lists, but don't know how. I have a vague idea that probably grep might be useful, but I don't know how to use it for this purpose.
So, to sum it up, what I would like to do is to take to text files containing lists and merge their common items into a third file in the form:

1 ItemA [value_from_list1] [value_from_list2]
2 ItemB [value_from_list1] [value_from_list2]
3 ItemC [value_from_list1] [value_from_list2]
4 ItemD [value_from_list1] [value_from_list2]

It would be great if someone might help me, thanks a lot!

---

### Post by seawolf167 on 2011-07-07
Maybe take a look at *diff*

```
man diff
```

this will compare files line by line for differences

---

### Post by sirverdemer on 2011-07-07
Thanks sewolf, I'll try that!

---

