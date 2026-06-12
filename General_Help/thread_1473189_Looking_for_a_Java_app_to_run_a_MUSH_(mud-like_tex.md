---
title: "Looking for a Java app to run a MUSH (mud-like text game)"
date: 2010-05-04
forum: General Help
---

### Post by Th3Professor on 2010-05-04
Hi!

I recently set-up a MUSH (Multi-User Shared Hallucination), which is kind of like a MUD (Multi-User Domain/Dungeon/etc.). Basically, it is a text-based RPG for roleplaying games the old fashioned way from back before the dawn of GUI/graphic user interface.

I would like to embed an application into my website to allow players (who don't want to download and run a separate mud/mush client program) to connect directly from the website.

I came across this:
[http://bc-dev.net/projects/fmud/fmud-demo/]("http://www.cre8asiteforums.com/redirect/jump.php?url=%2Fomed-dumf%2Fdumf%2Fstcejorp%2Ften.ved-cb%2F%2F%3Aptth")

Though, I have not been able to set it up to work with my site. Perhaps because that is a MUD app and not a MUSH app? I don't know if that is relevant. It is basically a telnet type of connection, and that uses Java, though I'm not sure what else there is to it.

Does anybody have any input on how I can get the text-based RPG accessible from a website?

Thanks!

 [IMG]http://www.cre8asiteforums.com/forums/style_emoticons/others/cheers.gif[/IMG]

---

### Post by zaphod777 on 2010-05-05
never heard of this before but this looks like it might work.

[http://www.scapefx.com/](http://www.scapefx.com/)

---

### Post by Th3Professor on 2010-05-06
> **zaphod777 said:**
> never heard of this before but this looks like it might work.

[http://www.scapefx.com/](http://www.scapefx.com/)

Thank you. I'll definitely look into that. It looks like they offer a "shareware" type of app, requiring advertisements unless purchased. I've contacted them to see about testing it out, though I'm wondering if there are possibly any others out there, any that are free.

Also, it looks like I might require some kind of Java coding knowledge to customize the settings on these things, though I know absolutely nothing about Java code. :???:

---

### Post by Th3Professor on 2010-05-23
It looks like I can use "FMud" for my MU* web browser (website embedded) java/etc. MUD/MUSH client for visitors at my site. However, I need to use my own custom install of the most recent version of Python for it to work. The main server that's hosting my site refuses to upgrade their python for some "compatibility issues across domains". So, what I'd like to know is...

How do I install python "locally" (such that it doesn't require root/sudo type access)?

(How do I install it just within my particular /home location within that server?)

Thanks! :)

---

### Post by zaphod777 on 2010-05-23
not sure if it is really possible but I know godaddy.com will give you a dedicated linux VM that you can have full control of if you pay extra. Or you could host the page yourself if you have an extra pc lying around or you could use a shiva plug. 

[http://plugcomputer.org/](http://plugcomputer.org/)

---

### Post by Th3Professor on 2010-05-24
> **zaphod777 said:**
> not sure if it is really possible but I know godaddy.com will give you a dedicated linux VM that you can have full control of if you pay extra. Or you could host the page yourself if you have an extra pc lying around or you could use a shiva plug. 

[http://plugcomputer.org/](http://plugcomputer.org/)

Can't pay extra or run separate hardware. It needs to be on the current primary server that holds everything else for the site.

Hmm... well I know that it is possible to install python locally. I was told by the creator of FMud that I can also just install python "locally" and bypass any root-related requirements. I just don't know how. I have googled it but not much luck there. I figured I'd use " --prefix=" but one page I found mentioned something about "make altinstall" instead of make install. It would make sense to use altinstall to not interfere with the main python on that server, though I'm not sure if I'd still need to add the --prefix flag to force it into a given location or if the altinstall will go ahead and do that. :confused:

---

