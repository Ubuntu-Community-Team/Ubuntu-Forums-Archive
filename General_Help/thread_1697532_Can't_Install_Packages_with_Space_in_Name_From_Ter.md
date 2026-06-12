---
title: "Can't Install Packages with Space in Name From Terminal"
date: 2011-02-28
forum: General Help
---

### Post by click.mine on 2011-02-28
Greetings All. I'm having trouble installing any packages with 2 or more words in their name. Single word ones install perfectly w/o any problems however. I've tried everything from quotation marks to backslash before the space but nothing seems to work & I keep getting the same Error. Here's an example (adobe air from software center):

steve@Vaio:~$ sudo apt-get install adobe\ air
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package adobe air

Thanks in  advance
Steve

---

### Post by dcstar on 2011-03-01
> **click.mine said:**
> Greetings All. I'm having trouble installing any packages with 2 or more words in their name. Single word ones install perfectly w/o any problems however. I've tried everything from quotation marks to backslash before the space but nothing seems to work & I keep getting the same Error. Here's an example (adobe air from software center):

steve@Vaio:~$ sudo apt-get install adobe\ air
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package adobe air

Thanks in  advance
Steve

That is **not** the package name, that is the package description. All package names are without spaces.

Use the GUI tools provided to install packages.

---

### Post by seawolf167 on 2011-03-01
> **dcstar said:**
> All package names are without spaces

This - find the correct package name and you'll be good to go.

Though you are using the escape character correctly so no worries there.

---

