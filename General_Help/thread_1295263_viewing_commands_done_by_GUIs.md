---
title: "viewing commands done by GUIs"
date: 2009-10-19
forum: General Help
---

### Post by dege_90 on 2009-10-19
Hi I've been using ubuntu for quite some time now and when ever I want to do something more advanced I always end up googling for the command to do it. That approach works and all but I figured that there gotta be a way to view what exactly the system and specific applications do at a given time. 

Like if I want to change desktop background, I'd right click on the desktop and choose Change Desktop Background and then add a new image and select it. Well that works great, no command line which makes it quick and easy without memorizing commands. 

But what if I want to write a script and want to know exactly what those clicks do? Which config file that gets edited or whatever to feature the new background. Google works...but as I said, I'd like to know if there's some kind of application that prints out all the actions a given gui does.

Would greatly appreciate some help on this matter.

---

### Post by OpenGuard on 2009-10-19
[http://mieszkancy.ds.pg.gda.pl/~zdzichu/backchanger.cs](http://mieszkancy.ds.pg.gda.pl/~zdzichu/backchanger.cs) - the art of search. By looking at this source code, you should be able to figure out, what you need to do to change your desktop background. Almost everything in Gnome goes through gconf, which works with xml files ( manipulate them with Pyhon or whatever you think is easier ).

---

### Post by dege_90 on 2009-10-19
Thanks for the reply but the desktop background was just an example. But would you say viewing source code would be a good approach in other cases?

---

