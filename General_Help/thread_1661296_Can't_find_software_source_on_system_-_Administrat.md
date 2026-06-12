---
title: "Can't find software source on system - Administration?"
date: 2011-01-06
forum: General Help
---

### Post by PastASide on 2011-01-06
So, i need to install wine and i can't find software sources to add a code. Please reply urgently.

:confused::confused:

---

### Post by Verbeck on 2011-01-06
> **PastASide said:**
> So, i need to install wine and i can't find software sources to add a code. Please reply urgently.
 
:confused::confused:
its hidden by default in 10.10
go to system>preferences>main menu and from the side bar, select 'administration' and check the item 'software sources'
or you can access it from the menu in the software center or synaptic
 
:instructions with screenshots [https://help.ubuntu.com/community/Repositories/Ubuntu#Missing%20repositories%20in%20Ubuntu%2010.10](https://help.ubuntu.com/community/Repositories/Ubuntu#Missing%20repositories%20in%20Ubuntu%2010.10)

---

### Post by PastASide on 2011-01-06
> **Verbeck said:**
> its hidden by default in 10.10
go to system>preferences>main menu and from the side bar, select 'administration' and check the item 'software sources'


Thanks you :guitar: Love ye!

---

### Post by PastASide on 2011-01-06
****, i can't install wine.

"Could not find package 'wine1.3'. :c help?

---

### Post by Verbeck on 2011-01-06
> **PastASide said:**
> ****, i can't install wine.

"Could not find package 'wine1.3'. :c help?
what instructions are you following? how far did you go? a link would help

and if you've already added the repository to the software sources correctly, from a terminal (applications>accessories) run:
```

sudo apt-get update
sudo apt-get install wine1.3

```

---

### Post by Tuomas on 2011-07-10
I'm on Natty and have the same problem, how do I get into software sources? :P Someone said you could get there from Ubuntu Software Centre, but I can't find it.

---

### Post by oldos2er on 2011-07-10
In a terminal, run **gksu software-properties-gtk**

---

