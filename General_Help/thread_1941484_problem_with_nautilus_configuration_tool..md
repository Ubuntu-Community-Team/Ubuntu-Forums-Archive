---
title: "problem with nautilus configuration tool."
date: 2012-03-15
forum: General Help
---

### Post by luissao88 on 2012-03-15
Hi,
my problem is: I need to open the nautilus config tool, and so i did.... or tryed, it started loading but it didn't open, so i removed it with the software centre and installed it again. Now i can't even find the app, although it's installed. i don't know what to do...

excuse my poor knowledge of english

---

### Post by Bobhuber on 2012-03-15
> **luissao88 said:**
> Hi,
my problem is: I need to open the nautilus config tool, and so i did.... or tryed, it started loading but it didn't open, so i removed it with the software centre and installed it again. Now i can't even find the app, although it's installed. i don't know what to do...

excuse my poor knowledge of english
What program are you talking about  (name ?)

---

### Post by mc4man on 2012-03-15
if you are referring to 'nautilus-actions' & on 11.10 then it was released broken & never fixed (inexcusable really

It's fairly easy to build but I guess you could use the getdeb repo to install
(I stopped paying attention to them when they closed off access to their source code/builds (or easily found access.

Main page (click on link to see how to use, you can't download .deb's directly
[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)


na page
[http://www.getdeb.net/updates/Ubuntu/11.10/?q=nautilus-action](http://www.getdeb.net/updates/Ubuntu/11.10/?q=nautilus-action)

---

### Post by luissao88 on 2012-03-16
my problem is that even if nautilus actions is installed (I tryed installing it by your link but it's the same) I can't find it (before i could, but anyway the program didn't work).

in fact what i want to do is to paste a file with admin mode, (i'm trying to install Age of Mythology (with wine) in my netbook, which has not cd reader and i need to paste the cd2 folder in z:)

---

### Post by Rick.B9 on 2012-03-16
Sometimes, when you can't find a program, you can go into Synaptic and search for a program, nautilus in this case, and click the "installed files" tab in the information part of the window at the bottom.  A file tree of installed files will appear, and you will look for a file in /usr/bin which provides the path to the executable.  Then you can open the file in a terminal like
```
/usr/bin/nautilus-actions-config-tool &
```The & at the end will allow the terminal to continue to be used, and keep the config-tool open even if you happen to shut down the terminal.

I'm not sure if this is what you're looking for, but it should give you an idea how to find the command to launch a program if you can't find it and the "which" or "whereis" commands aren't helping you.

---

### Post by luissao88 on 2012-03-17
> **Rick.B9 said:**
> Sometimes, when you can't find a program, you can go into Synaptic and search for a program, nautilus in this case, and click the "installed files" tab in the information part of the window at the bottom.  A file tree of installed files will appear, and you will look for a file in /usr/bin which provides the path to the executable.  Then you can open the file in a terminal like
```
/usr/bin/nautilus-actions-config-tool &
```The & at the end will allow the terminal to continue to be used, and keep the config-tool open even if you happen to shut down the terminal.

I'm not sure if this is what you're looking for, but it should give you an idea how to find the command to launch a program if you can't find it and the "which" or "whereis" commands aren't helping you.

Thank you! you solved my problem
That's what I love about ubuntu, everyday i learn something new

---

