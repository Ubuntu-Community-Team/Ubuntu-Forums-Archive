---
title: "location of apps installed in ubuntu 11.10"
date: 2011-11-10
forum: General Help
---

### Post by tadkin on 2011-11-10
Ok here Goes 

This is my first time for using ubuntu ever.
I would have to say WOW, what an fantastic experience.

I have installed Ubuntu for a specific purpose, that is, I have a web site that has been developed which is going to be used for the purpose of using a touch screen in a kitchen which will run a Database of recipes through open office dbase as well as other apps like a timer and the lilke.
The web site has icons that look much like an Iphone, the idea being you touch the icon and it opens what you need.

My question is this, The web site has been developed ( dare i say it here ) for windows this means all the hyper links and links to apps are pointing to directories as you would normally see for a windows install ( C:program files etc.....). 

I would like to start to understand when i install apps on ubuntu where are they installed so i may be able to then edit the hyperlinks for the apps in the source code of the page and have them open when i touch on the icon.

This may seem like a newbie question and i suppose it is, any help on this would be most appreciated.
I am installing the apps using the software manager gui interface.

Ubuntu Version 11.10

Thanks 
Ken
Tadkin

---

### Post by nothingspecial on 2011-11-10
Usually in /usr/bin but not always.

To find out type ```
which <app>
```

eg

```
nothingspecial@spell-book:~$ which firefox
/usr/bin/firefox
nothingspecial@spell-book:~$ which guayadeque
/usr/bin/guayadeque
nothingspecial@spell-book:~$ which which
/usr/bin/which

```

---

