---
title: "how to boot w/o compiz"
date: 2009-08-07
forum: General Help
---

### Post by bandofmercy on 2009-08-07
Knowing it probably caused problems in the past, I tried to enable blurring in my simple-ccsm and froze my wind netbook in the process.  now when i boot up i usually get a desktop, but can't click anything and it quickly goes black--i'm guessing the blur effect is still enabled and causing problems.   i believe this is a bug with the intel 945 graphics stuff.

i have no safe graphics mode in my boot options and autologin turned on.  how can i boot with compiz turned off so i can disable blurring?  thanks in advance.

---

### Post by bandofmercy on 2009-08-07
so basically i want to know how to disable automatic login (so i can login in safe graphics mode) or compiz FROM THE COMMAND PROMPT.  help???  i'm on jaunty right now.

---

### Post by fooman on 2009-08-07
> **bandofmercy said:**
> so basically i want to know how to disable automatic login....

to disable automatic login,  go to administration > login window

click the security tab and *un*-check "enable automatic login".

---

### Post by Zeroangel on 2009-08-07
Well offhand I would try using CTRL+ALT+F1 to go into the console mode. And then from there try this command:
```
sudo dpkg-reconfigure compiz
sudo dpkg-reconfigure compiz-plugins
```
And see if that resets everything to the defaults for you.

---

### Post by fooman on 2009-08-07
to disable compiz...go to preferences > appearance > visual effects tab

set to "none".

hope that helps.

---

### Post by bandofmercy on 2009-08-07
> **fooman said:**
> to disable automatic login,  go to administration > login window

click the security tab and *un*-check "enable automatic login".

no, i want to disable it from the command prompt... using gconftool perhaps?  but i can't find specifically how.

---

### Post by bandofmercy on 2009-08-07
OH, and dpkg-reconfigure compiz's didn't work either, btw.  thanks for your continued efforts...

---

### Post by bandofmercy on 2009-08-07
is there a way to start gdm from the cli in safe graphics mode?

---

### Post by wojox on 2009-08-07
Reboot and press Esc key while your in the three second count down.

---

### Post by bandofmercy on 2009-08-07
i have no gdm login.  it goes straight from grub to loading to the desktop.

---

### Post by wojox on 2009-08-07
In between bios and grub should be a three second counter to choose which kernel to load. Reboot and press the Esc key a bunch of times. Or boot a Live CD and change it that way.

---

### Post by bandofmercy on 2009-08-07
What is this escape suppoesed to do?  i press it over and over and still enter my grub screen w/ various kernels, windows, memtest... no safe mode there though. am i supposed to enter the grub> command prompt?

---

### Post by Universal344 on 2009-08-07
If there are no recovery mode kernel options in the GRUB menu than go back into the command prompt after a restart and just try uninstalling compiz (make sure to completely uninstall it using the purge option)and then see if you boot fine.

---

### Post by bandofmercy on 2009-08-07
solved...
ctl alt f2
```
metacity --replace --display :0 &
```

while gnome is  still running.  then switch back w/ ctl alt f7 and fix your compiz or whatever.

thanks for all your help!

---

