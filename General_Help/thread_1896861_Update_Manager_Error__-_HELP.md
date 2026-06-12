---
title: "Update Manager Error  - HELP"
date: 2011-12-17
forum: General Help
---

### Post by mattpyle82 on 2011-12-17
I get this error message when trying to run Update Manager.  If someone could give a step by step fix it, I'd be grateful.  I'm still fairly new to Ubuntu.

E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Thanks to anyone with some insight :)

---

### Post by bluexrider on 2011-12-17
> **mattpyle82 said:**
> I get this error message when trying to run Update Manager.  If someone could give a step by step fix it, I'd be grateful.  I'm still fairly new to Ubuntu.

E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Thanks to anyone with some insight :)
Lets not get crazy here just yet.

open a terminal and run this 

```
sudo apt-get update && sudo apt-get upgrade
```

If you have errors please post

---

### Post by mattpyle82 on 2011-12-18
> **bluexrider said:**
> Lets not get crazy here just yet.

open a terminal and run this 

```
sudo apt-get update && sudo apt-get upgrade
```If you have errors please post

just ran it and i get this error

E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)

---

### Post by wildmanne39 on 2011-12-18
Hi, open your source list and look at line 54 and see what is wrong with it, you may be able to just remove it.

Use this command in the terminal to open the source list.
```
cat /etc/apt/sources.list
```

---

### Post by bluexrider on 2011-12-18
> **mattpyle82 said:**
> just ran it and i get this error

E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)

```
sudo gedit /etc/apt/sources.list
```

scroll to line 54 and add # to the beginning of the line. This will comment-out the line and will not be used during updates.

You should also be able to compare that line with another one to check the differences and the cause of the problem

---

