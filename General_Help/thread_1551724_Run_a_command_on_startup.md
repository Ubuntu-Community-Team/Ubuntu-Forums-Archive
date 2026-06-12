---
title: "Run a command on startup"
date: 2010-08-12
forum: General Help
---

### Post by BrianG007 on 2010-08-12
Hello, I am trying to run a command at the startup of Ubuntu to load a touchscreen driver and read the config file. Here is how I would manually do it in the terminal:

sudo /usr/local/Gentouch_S/GT_service start

Then I enter the root password and the driver loads and my touchscreen has saved calibration from the config file that the GT_service reads.

Now how can I set this command to load at startup?

The readme file has the below info in it but I am new to Linux and Ubuntu and I dont understand.

FROM README FILE:
add the following script to your own xinitrc file to let the driver start automaticly everytime you reboot:(ubuntu is too different from others!)          
'if [ -e /tmp/.GTInstallPath ];then `cat</tmp/.GTInstallPath`/GT_service restart;else /usr/local/Gentouch_S/GT_service restart;fi;

Please help me!

---

### Post by earthpigg on 2010-08-12
hi,

based on the information you provided (& assuming it is all accurate), running these commands in the terminal ought to do it:

1) make a backup of the file we are about to modify:
```
sudo cp /etc/X11/xinit/xinitrc /etc/X11/xinit/xinitrc-backup
```

2) open the file in text editor:
```
sudo gedit /etc/X11/xinit/xinitrc
``` 

3) open the readme file in the text editor in a different tab. copy and paste the stuff from the readme to the end of that file, without changing anything that is already there.

so, it currently looks something like this:
```
#!/bin/bash

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
```

and we make it look like this:
```
#!/bin/bash

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

the stuff you paste goes here

```



4) save.

5) reboot.

if you want to undo this because it didn't work, we delete the file we modified and restore the backup:
```
sudo rm /etc/X11/xinit/xinitrc
sudo cp /etc/X11/xinit/xinitrc-backup /etc/X11/xinit/xinitrc
```

---

### Post by bodhi.zazen on 2010-08-12
Using any editor, open xinitrc

```
gedit ~/.xinitrc
```

Copy / paste that line at the bottom of the file (it may be empty).

Save the file.

Reboot.

You probably can simply log of and back in without rebooting, this is Linux, seriously rebooting sooooo .... Windows.

Post back if you have a problem with that.

---

### Post by earthpigg on 2010-08-12
bodhi.zazen's method and mine are nearly identical, you can pick which one you want to use.

my method can cause more damage if the readme file is incorrect, or if you do it wrong... but it will work for all users on that computer.

his method will only work when you log in with ***your*** username, and you will have to do it for each person's login if you want them to also be able to use the touchscreen. 

pick which you prefer. if you are the only one that ever uses this computer, go with his method.

---

### Post by BrianG007 on 2010-08-12
Thank you all for the quick responses. I will try to get this working first thing tomorrow morning. I will post an update tomorrow.
Thanks!

---

### Post by BrianG007 on 2010-08-13
Well I tried the two methods above and unfortunately neither worked. How could I set up this command to run at startup:

sudo /usr/local/Gentouch_S/GT_service start

Detailed instructions appreciated for Ubuntu 10.4

---

### Post by Noz3001 on 2010-08-13
Can't you call it from /etc/rc.local?

---

### Post by BrianG007 on 2010-08-13
I found the rc.local file and has some text that says by default this script does nothing... then there is an exit 0 at the bottom. How do I place the command in here for it to run at startup?

---

### Post by bodhi.zazen on 2010-08-13
> **BrianG007 said:**
> I found the rc.local file and has some text that says by default this script does nothing... then there is an exit 0 at the bottom. How do I place the command in here for it to run at startup?

Put your command, without the sudo part, above the "exit 0" .

The biggest problem with that is rc.local may run too soon (due to "concurrency" in an attempt to speed boot times) so you may need to add a sleep.

sleep 10
command ...

You can reduce the sleep as needed.

---

### Post by Firedrake445 on 2010-08-13
Couldn't you go to System>Preferences>Startup Applications and then go to add to make the command run?

---

### Post by cyqan on 2011-06-18
Hi, 

sorry for my poor english :/


I've the same problem.
Did you fix the problem?

Whether I add the string below to xinit or into the rc.local:

--------------------------------------------------------
sudo /usr/local/Gentouch_S/GT_service start
sleep 10;
--------------------------------------------------------

the calibration only works for the 10 second.

The string from README FILE don't work


How can I start this service automatically after login?

Help...

---

