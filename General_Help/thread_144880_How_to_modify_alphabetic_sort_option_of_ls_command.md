---
title: "How to modify alphabetic sort option of ls command?"
date: 2006-03-15
forum: General Help
---

### Post by chugru on 2006-03-15
Hi, All...

I am new to Kubuntu, but, so far I am very pleased.

There is one modification I would like to make regarding the way the **ls -l** sorts a directory list alphabetically.

Currently, Kubuntu sorts by following a pattern in which all files are collated listing "number" file names first, directories last, and bunching "all other files" into a list, ignoring case and ignoring the presence of non-alphabetic characters within file names.

I would like the "all other files" to be further sorted upper case first and nonalphabetic characters (or spaces) to be listed before alphabetic characters.

Would someone please tell me how to set this up?? :D 

Thanks!

---

### Post by mr_mop on 2006-03-15
Try an **ls --help** to see the variety of options that ls takes.

---

### Post by chugru on 2006-03-15
[QUOTE=mr_mop]Try an **ls --help** to see the variety of options that ls takes.[/QUOTE]

I did that, but none of the options sort in the manner I want... :(

Which config file sets the ls default sort pattern?

---

### Post by feathers on 2006-03-16
You could pipe the ls output to the sort command and see what it can do for you. ls -l | sort. Look at man sort to find the appropriate options.

---

