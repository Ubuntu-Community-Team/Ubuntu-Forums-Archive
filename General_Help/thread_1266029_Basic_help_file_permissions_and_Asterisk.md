---
title: "Basic help file permissions and Asterisk"
date: 2009-09-14
forum: General Help
---

### Post by edwardsmj on 2009-09-14
I'm new to Linux (again), frustration usually makes me format my hard drive (Using DOS, if I tried to do it in Linux my head might explode).
 
To use Linux I know you must read, read, search, read ....... and to run one application can become a 4 day process.
 
I'm trying to edit .conf files at the moment using the desktop to try to open them - how do I set permissions, I thought it might be a drop down but I can't find it.
 
I'm trying to get Astrisks working, I'm on the password setting bit does any one know a site that has a true idiots guide, with out statement like create a file in the **.d directory without telling you what the file should be called and what syntax to use.
 
Thanks.
 
All I want to do is edit files using the desktop specifically the .conf files in /etc/asterisk/ I can use the command line to sudo gedit, but I want to open the file in a text editor using the desktop GUI but they are not available.
 
I don't want to touch the command line to be able to edit a file, all I want to do is choose my directory, right click file, open with editor application and click a permissions drop down and enter SU password
 
 
For Asterisk I'm setting it up for the first time it seems to be running in the background I'm trying to run a front end GUI (not sure which is the best) but it says it need to have a password configured in 3 .conf files before you can use Asterisk
 
 
 
Thanks for [[COLOR=#444444]nautilus-gksu[/COLOR]]("apt:nautilus-gksu") It seems strange that Ubuntu does not include this functionality as standard, although there must be a very good reason. This has always been the challenge with Linux it includes references to make things work, even the most intuitive operations need a new application installed with the layers of problems that may cause.  It reminds me of the adventure books you got years ago, at the end of the page it would say to turn left at the pillar of gold turn to page 63, to turn right turn to page 101.

---

### Post by nothingspecial on 2009-09-14
What are you trying to accomplish?

---

### Post by scragar on 2009-09-14
OK, I really want to help here, but you are being rather vauge with your problem, is there any way you can explain what you are trying to do and having problems doing?

As for getting perms to edit files, if your normal user doesn't have perms think of that as a warning that you should be careful with what you are doing, then go ahead and run:```
gksu gedit
```from either a terminal(applications>accessories>terminal) or the run box(press ALT+F2 at the same time).
It will ask for your password to confirm that you really want to grant root privileges to the text editor.

---

### Post by CatKiller on 2009-09-14
I think [nautilus-gksu]("apt:nautilus-gksu") is what you're after.

---

