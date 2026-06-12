---
title: "Custom Launcher in Natty Unity Desktop"
date: 2011-05-19
forum: General Help
---

### Post by pjrodz on 2011-05-19
Hi! I'm trying to put in an extra command on my skype.desktop launcher to make my webcam work properly, however whenever I add the ff. to the Exec line:

> Exec=export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

the skype launcher doesn’t work. However, it works fine when I try to run the same command on the terminal. Any thoughts on this? thanks!

---

### Post by kerry_s on 2011-05-19
You'll need to put that in a script, *.desktop files only does single command or path, it won't do anything past the first word.

---

### Post by pjrodz on 2011-05-19
> **kerry_s said:**
> You'll need to put that in a script, *.desktop files only does single command or path, it won't do anything past the first word.

thanks for the reply, btw do you have links that teach users on how to make scripts? thanks again! :)

---

### Post by wildmanne39 on 2011-05-19
> **pjrodz said:**
> thanks for the reply, btw do you have links that teach users on how to make scripts? thanks again! :)

HI,click on power user guide below this text and it will tell you how to create shortcuts and many other things too.

---

### Post by pjrodz on 2011-05-19
> **wildmanne39 said:**
> HI,click on power user guide below this text and it will tell you how to create shortcuts and many other things too.

thank you for the wonderful link man! however, i can't seem to find the topic that shows how to put in commands/scripts on the Exec line of the .desktop file.

---

### Post by jerome1232 on 2011-05-19
Simply make an exectuable script (use gedit) save it as skype-launcher.sh

```
#!/usr/bin/sh
Exec=export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so
skype
```

Right click it, make sure it's set as exectuable under the permissions tab.

Create a custom launcher, make the command to exec be "/home/youruser/skype-launcher.sh"

should work

---

### Post by wildmanne39 on 2011-05-19
> **pjrodz said:**
> thank you for the wonderful link man! however, i can't seem to find the topic that shows how to put in commands/scripts on the Exec line of the .desktop file.
Hi, here are 2 links that were on that page one of them should be what you want.
[http://askubuntu.com/q/13758/235](http://askubuntu.com/q/13758/235)
[http://askubuntu.com/q/34597/235](http://askubuntu.com/q/34597/235)

---

### Post by pjrodz on 2011-05-19
thanks everyone for your replies! it's working now :D

this link was also very useful in creating linux scripts:
[http://www.ax697.org/writing-a-basic-ubuntu-script-200786.html]("http://www.ax697.org/writing-a-basic-ubuntu-script-200786.html")

i saved the script on my home folder then proceeded to update the skype.desktop file in /usr/share/applications

> $ cd /usr/share/applications
$ sudo gedit skype.desktop
 

then i placed this on the Exec line: > Exec=./myscript.sh

save then close. that's it woohooo!

---

### Post by pjrodz on 2011-05-19
> **jerome1232 said:**
> Simply make an exectuable script (use gedit) save it as skype-launcher.sh

```
#!/usr/bin/sh
Exec=export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so
skype
```

Right click it, make sure it's set as exectuable under the permissions tab.

Create a custom launcher, make the command to exec be "/home/youruser/skype-launcher.sh"

should work

it worked! thanks man!

---

### Post by fishbulb1022 on 2011-07-24
Just a tip in case in the future you don't want to write and save a script, you can run multiple commands like this:

sh -c "<command1> & <command2>"

Note the single ampersand which allows you to run both commands simultaneously. A double ampersand (&&) allows you to run one, and then the next. In other words, it executes the second after the first has finished. For example, I run 

sh -c "amixer set Line unmute & (tvtime && amixer set Line mute)" 

when I want to watch tv with tvtime. For some reason, tvtime can't access my mixer to unmute line on its own, but the above command allows me to run amixer set Line unmute and (tvtime && amixer set Line mute) at the same time. The second command is itself a compound command and it (with the double ampersand) mutes line when tvtime finishes, which is when I close it.

---

