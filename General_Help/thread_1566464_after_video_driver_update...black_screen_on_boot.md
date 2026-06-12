---
title: "after video driver update...black screen on boot"
date: 2010-09-02
forum: General Help
---

### Post by harperjo86 on 2010-09-02
My Machine: Lenovo T400 laptop, 9.04 ubuntu
My problem: while working on my laptop the system Offered an update to my ATI video card............so being the nube that I am I said go ahead and install it............yep that f'd it up.  it ran for a while then froze up to the point I had to hard boot the machine.  on restart the desktop splash/load screen displays but nothing else afterwards.  I can get into restore mode and even terminal but can't seem to find anything to help out........there is an autofix video option but that did not work either.
 
I spent a week loading and configuring this thing and do not want to start back from scratch...........I have too much stuff to lose on a new install.  funny thing is that I just had set the system to do a complete backup of the ubuntu instance for tonight so I would have some way to restore this if something happened...........well it happend before the backup ran tonight........go figure.
 
help me out if you can......is there a way to reload the default system without loosing my files and such?  I would just have to load vmware back on and some other programs but I a okay with that.

---

### Post by Chris1274 on 2010-09-02
A lot of people have been having the same problem. You need to uninstall the proprietary driver and use the open source one instead.
```
sudo apt-get remove fglrx
```

---

### Post by harperjo86 on 2010-09-02
Thanks for the reply..........what does this script do...........reload the default video driver? or uninstall the current driver........or both?  complete nubie on Terminal lingo.

---

### Post by harperjo86 on 2010-09-02
no good..........I ran the script in the recovery terminal with network
 
sudo apt-get remove fglrx
 
but got the repoly that package fglrx did not exist.......so back to square one.  anybody else want to chime in? or have came across a thread that might help.

---

### Post by Mark Phelps on 2010-09-02
Don't think that command is correct ...

Look in the link below, in the section about removing the proprietary driver, for the proper commands:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by ninhalo5 on 2010-09-02
sorry, don't mean to hijack the thread, but when I try to do any of that I get a notice saying everything on my drive is read only. I accessed the prompt through the recovery mode normal boot option. nothing can connect to x server and I'm not allowed to remove anything even under sudo. I installed a theme tonight that totally fried my os now it looks as I'm going to loose everything and restore the system :(  I'm actually using 10.04 Lucid

---

### Post by Chris1274 on 2010-09-02
> **Mark Phelps said:**
> Don't think that command is correct ...
 
Look in the link below, in the section about removing the proprietary driver, for the proper commands:
 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
Oops. I was going off what I had read elsewhere. Looks like the proper command is
```
sudo apt-get remove --purge xorg-driver-fglrx
```
When mine got screwed up I just reinstalled the OS, only to find out later that the driver could be removed.

---

