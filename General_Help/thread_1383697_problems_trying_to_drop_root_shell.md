---
title: "problems trying to drop root shell"
date: 2010-01-17
forum: General Help
---

### Post by shaunfromthewildwoods on 2010-01-17
hello,  

new to Ubuntu 9.10,  using a macbook,  

having "could not update ICe authority file" problem on start up. trying to fix it with solution in this thread.
 [http://ubuntuforums.org/showthread.php?t=94975](http://ubuntuforums.org/showthread.php?t=94975)

when boot in recovery mode to drop root shell,  i get  a failure to mount file systems errors and a bunch of other jargon text appear on the screen,  arrow keys don;t work to navigate to drop root shell,  

any help is much appreciated

edit*

should add that this seemed to be the result of wolfenstein enemy territory crashing,  after clicking the ICE authority dialog box, ubuntu boots as normal,  everything seems fine once running

---

### Post by Leppie on 2010-01-17
can you boot into a normal session?

---

### Post by cariboo on 2010-01-17
I looked at your post earlier, and I passed it up due to lack of info, but I see by your edit you had a crash. Boot from the Live CD, once at the desktop open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -a /dev/sda
```

Substitute your hard drive for /dev/sda, once fdisk is finished you should be able to start as normal.

---

### Post by shaunfromthewildwoods on 2010-01-17
I have no problem booting up as normal,  on ubuntu right now and working fine,  just wondering about the ICEauthority error message on start up,  

trying to boot from live cd but get black screen with blinking underscore

---

### Post by Monotoko on 2010-01-17
that sounds like a faulty burn to me...have you tried the disk in another computer?

---

### Post by Leppie on 2010-01-17
if you want to get to a root shell, you can get there from within your normal environment:
```
sudo -i
```

---

### Post by shaunfromthewildwoods on 2010-01-17
now getting this on boot up,  right before login screen

one or more of the mounts listed in /etc/fstab cannot be mounted: swap= waiting f UUID=d4d71cbe-bcdd-4deb-85ae-8305 9cd2f028
Pres ESC to enter a recovery shell


after pushing ESC and logging on, everything still works fine

---

### Post by Leppie on 2010-01-17
was it only wolfenstein that crashed, or the whole system?

---

### Post by shaunfromthewildwoods on 2010-01-17
whilst playing wolfenstein after pushing esc key, whole system crashed

---

### Post by shaunfromthewildwoods on 2010-01-18
okay, so fixed ICE authority through this code found in another thread,

sudo chown shaun\: ~/.ICEauthority

solved now,

---

