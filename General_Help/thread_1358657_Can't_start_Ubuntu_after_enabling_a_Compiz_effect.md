---
title: "Can't start Ubuntu after enabling a Compiz effect"
date: 2009-12-18
forum: General Help
---

### Post by ok_dr on 2009-12-18
Help! I suddenly can't start Ubuntu. I was looking at Compiz options and when I checked on effects "enable reflections" (or something similar I don't recall it exactly)suddenly everything froze. I had to press the shutdown down button, but when after I tried to turn my computer back on now it freezes at the usplash screen, nothing happens.
Any advice?

---

### Post by ubudog on 2009-12-18
It seems that you have seriously messed up your hard drive.  To fix this: Start the computer with an Ubuntu LiveCD.  At the menu, select "Repair an existing installation".  Follow the onscreen instructions.  If you need any more help just ask.

---

### Post by DeMus on 2009-12-18
> **ok_dr said:**
> Help! I suddenly can't start Ubuntu. I was looking at Compiz options and when I checked on effects "enable reflections" (or something similar I don't recall it exactly)suddenly everything froze. I had to press the shutdown down button, but when after I tried to turn my computer back on now it freezes at the usplash screen, nothing happens.
Any advice?

I hope you've learned your lesson about Compiz. Many problems can be related to the use of Compiz and still people keep using it, after which they come here to complain: Ubuntu acts funny.
No, you installed Compiz and that is f*cking up your graphic system.

---

### Post by ubudog on 2009-12-18
Demus is right.  To fix this, you will have to remove compiz.  To do this, since you have no access to your desktop, you have to boot into recovery mode and drop to a root shell.  Once you get to the grub menu, select the kernel with "Recovery mode" at the end of it.  Once it boots up and you get to the menu, select "Drop to root shell", you will see a command line.  Type ```
sudo apt-get remove compiz
```.  Restart your computer, and everything should work.  Good luck.  EDIT: You may not have desktop effects, but your computer will work.

---

### Post by ok_dr on 2009-12-18
Removing Compiz didn't do it for me. As for "repairing an existing installation" I can't seem to find this option on the live cd.

---

### Post by ubudog on 2009-12-18
> **ok_dr said:**
> Removing Compiz didn't do it for me. As for "repairing an existing installation" I can't seem to find this option on the live cd.

The repair an existing installation option is on the menu of the livecd before you actually boot it.  It is the last on the list.

---

### Post by ok_dr on 2009-12-18
> **ubudog said:**
> The repair an existing installation option is on the menu of the livecd before you actually boot it.  It is the last on the list.

I'm afraid it's not. The options on the menu are

Try Ubuntu without installing
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk (this is the last option which just boots my current installation and than naturally freezes)

---

### Post by ok_dr on 2009-12-18
Ok I made it. 
I deleted the folders Compiz from folders .config, .gconf/app or any other folder named compiz on my home directory, also deleted those compiz files which still were on /usr/bin.
Not a very elegant solution I guess but it got the job done.

Thanks for your time ubudog.

By the way though probably DeMus may be right I don't like the tone used to remark it. You can't blame a Ubuntu user for trusting a software found on the official repositories.

---

### Post by ubudog on 2009-12-18
You are welcome.  If you need any help with anything, just private message me.

---

