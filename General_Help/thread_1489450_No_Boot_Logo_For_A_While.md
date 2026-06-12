---
title: "No Boot Logo For A While"
date: 2010-05-21
forum: General Help
---

### Post by Jakiejake on 2010-05-21
Hey,
When I boot Ubuntu 10.04 Lucid Lynx my computer goes through the POST check and all that then boots from the HDD
When it's booting the OS all I see is a black screen with "_" flashing on it (without quotes) then a few seconds after I see the Ubuntu logo then the log-in screen appears
It's not a problem, just weird and annoying
Please Help...

---

### Post by Jakiejake on 2010-05-23
Bump

---

### Post by Jakiejake on 2010-05-24
BUMP!!!
Any Answers? :confused:

---

### Post by John Bean on 2010-05-24
> **Jakiejake said:**
> BUMP!!!
Any Answers? :confused:

Yes: it does that.

---

### Post by WorMzy on 2010-05-24
From the [known problems/workarounds sticky]("http://ubuntuforums.org/showthread.php?t=1469475") at the top of the forum:

Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```

---

### Post by Jakiejake on 2010-05-25
> **WorMzy said:**
> From the [known problems/workarounds sticky]("http://ubuntuforums.org/showthread.php?t=1469475") at the top of the forum:

Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```


Thank you
I just did it and will look tomorrow when I start my computer again (it's night time here in Australia)
I'll post a reply tomorrow
Oh and i'm pretty sure I read that thread
Never mind
So i'll post tomorrow
Wish Me Luck

---

### Post by Jakiejake on 2010-05-26
Worked
Thread Marked As Solved
Thank You Everyone

---

