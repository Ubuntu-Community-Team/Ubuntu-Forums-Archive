---
title: "System running in low res"
date: 2012-07-29
forum: General Help
---

### Post by old farmer on 2012-07-29
Im having the problem of 'your screen, graphics card and input devices could.......
I dont recall up dating. 
My system grub:
ubuntu 12.04 LTS, kernal 3.2.0-25-generic.....

I haved looked at a few threads and did the following
sudo apt-get install fglrx
but that didnt fix anything (obvious)

When I run from  live cd, the screen works fine
lspci | grep VGA returns
00:02.0 VGA compatible controller: Intel corporation 82945G/GZ intigrated graphics controller (rev 02)

I have looked in etc/X11 but there is no xorg.conf, but there are lots of xorg.conf.dist-upgrade.... files

any help, or direct me to a thread that will help
thanks
jeffrey

---

### Post by old farmer on 2012-07-31
Still waiting for HELP  :confused:

---

### Post by old farmer on 2012-08-13
.

---

### Post by Nardon on 2012-08-13
Hey,

What video card do you have? I am seeing something strange in this line:
```
00:02.0 VGA compatible controller: Intel corporation 82945G/GZ intigrated graphics controller (rev 02)
```

It suggests that it is only seeing the integrated graphics chip and doesn't see your video card.

---

### Post by old farmer on 2012-08-16
video card?
What ever came in this Lenovo desktop (IBM)
what command do I put into terminal for that?
keep in mind im running from a live disk...

---

