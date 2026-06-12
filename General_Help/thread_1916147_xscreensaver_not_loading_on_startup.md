---
title: "xscreensaver not loading on startup"
date: 2012-01-27
forum: General Help
---

### Post by Pro$pect on 2012-01-27
I added "xscreensaver -nosplash" to my startup applicatons but it is not running on start up. I get this error when I go so the screensaver settings: the Xscreensaver daemon doesn't seem to be running on display ":0".Launch it now?   
If I launch it, it's fine.  I wonder how I can correct this ?

---

### Post by hwttdz on 2012-01-27
How did you solve it?

---

### Post by andreigh on 2012-05-15
May be you have to add
/usr/bin/xscreensaver -nospalsh
?

---

### Post by Jedcurtis on 2012-09-04
The first time you run the XScreenSaver application from your applications menu, (this is actually xscreensaver-demo I believe, which if you've installed correctly you can actually type from a terminal) it should create a .xscreensaver file in your /Home directory.  (Anytime you or the system puts a . in front of a folder or file, it makes it "hidden", so to see hidden files from Nautilus for example, just hit Ctrl-H to see them.)  This is actually the "GUI" for the xscreensaver app where you can choose which screensaver, the time you want it to wait before appearing, etc...
Once you can see that that file is actually there (the .xscreensaver) you should be able to go to your Startup Applications, click on add,  'Name' it whatever you want, in the 'Command' you need to type "**xscreensaver -nosplash**" (without quotes!), then in the 'Comment' just type in something like "this starts the screensaver daemon in the background"  (again, you don't need the quotes!)
This should solve the issue for you!  A screenshot below shows the one I use that works perfect!

Thanks,
Jed

[IMG]http://www.jedsdesk.com/tmp/Edit%20Startup%20Program.jpg[/IMG]

---

