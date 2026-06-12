---
title: "How to run a command application from desktop?"
date: 2011-02-18
forum: General Help
---

### Post by Pollyanna1 on 2011-02-18
I have download many applications that run from the terminal. and I can not access them directly from my computer without remember the name of the application and type it into the terminal. Some of them are just the name of the application but some of them are many commands into one line.
So is there any way to add them under the application menu or desktop? I tried the luncher but it does not work.

---

### Post by dcstar on 2011-02-19
> **Pollyanna1 said:**
> I have download many applications that run from the terminal. and I can not access them directly from my computer without remember the name of the application and type it into the terminal. Some of them are just the name of the application but some of them are many commands into one line.
So is there any way to add them under the application menu or desktop? I tried the luncher but it does not work.

Simply create a Launcher with "Application in Terminal".

---

### Post by PaulReaver on 2011-02-19
can i ask what app you're trying to run?

you could put it in a script


#!/bin/sh
<terminal command goes in here>
exit

---

### Post by Pollyanna1 on 2011-02-19
for example 
I need to run this application :
jbidwatcher

and this video streaming 
rtmpdump -v -r rtmp://livestfslivefs.fplive.net/livestfslive-live/ -y  "aljazeera_ar_high" -a "aljazeeraflashlive-live" -o -| mplayer -

---

### Post by PaulReaver on 2011-02-19
about the ebay watching app.... I can't help as I don't have any experience 

Sorry.


If the aljazeera live feed is always at the same address
in a terminal paste this (the whole lot is one line)

echo '#!/bin/sh
> rtmpdump -v -r rtmp://livestfslivefs.fplive.net/livestfslive-live/ -y "aljazeera_ar_high" -a "aljazeeraflashlive-live" -o -| mplayer -' > ~/Desktop/aljazeeralive.sh 

then paste this into the terminal

chmod +x ~/Desktop/aljazeeralive.sh


an executable script should now be on your desktop... you can double click it... you'll need to use the system monitor if you want to stop it though.

hope it helps

---

### Post by Pollyanna1 on 2011-02-19
It does create the shortcut on the desktop. but when I run it, new file created (rtmpdump) instead of playing the live channel.

---

### Post by Krytarik on 2011-02-20
Check if you have the correct command in the script file:
- double-click at it
- click at display

If it really doesn't work without the terminal, create a launcher for it instead, and since the "Application in Terminal" option doesn't work currently
- choose "Application" and
- set the command like this:
```
gnome-terminal -x sh -c "terminal_command"
```

---

### Post by Pollyanna1 on 2011-02-20
Thank, 

It works now.. 

and here I just rewrite it in steps.

1- Create empty file any whare in your computer

2- add the command in that file for example to run the bid watcher just type the command
 jbidwatcher

3- make that file executable.

Done.

---

