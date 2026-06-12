---
title: "How to remove windows?"
date: 2010-08-26
forum: General Help
---

### Post by dishayu on 2010-08-26
Hello everyone.

I installed ubuntu 10.04 on to my system a few months back. It was a wubi installation (install inside windows). Now i have gotten around to liking it a lot. I want to completely remove windows from my system now. How do i do that?

Please note that it's a WUBI

I posted here for help because i do not have a working CD drive as of now, so i need to get it right in 1 try. My windows and ubuntu installation are on the same physical partition (C drive in windows).

I am guessing i'll have to do something about the bootloader too, when i remove windows? Because i boot using the windows bootloader right now.

Many Thanks

---

### Post by mikewhatever on 2010-08-26
Given the circumstances, I don't think removing Windows is a good idea. Without the working cdrom and Windows, if Ubuntu stops working, you are toast.

---

### Post by Zimmer on 2010-08-26
Quick reply... you cannot, at the moment, as WUBI is 'running Ubuntu inside Windows'.

As you have no working CD drive you will need to investigate installing Ubuntu from an external drive/USB stick or other external CD/DVD drive you can obtain.
See the community and official documentation for some pointers..
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

These pages do not appear to be responding currently, though.

---

### Post by 3Miro on 2010-08-26
In the case of wibi, removing windows will remove Ubuntu. You should make a clean install of Ubuntu from a USB (after backing up everything important since you will wipe out the entire system).

---

### Post by elliotn on 2010-08-26
Get a friend who has a CD drive and use Unebootin to create an ubuntu bootable usb drive.
Use the flash drive to install ubuntu and choosing use entire disk in your install so u can get rid of windows

---

### Post by UniWoozle on 2010-08-26
What you are trying to do is like removing the chassis of a car, and leaving the engine behind and expecting it to run and move.

---

### Post by quizno50 on 2010-08-26
What I would suggest is backing up your home directory; then just doing a fresh install of Ubuntu (see above posts for flash-drive method). Unlike windows; on Ubuntu backing up your home directory saves your profile exactly as it should be (**all** programs' preferences are stored there).
The only problem would be backing up your installed programs, but there's gotta be a way to do a list of installed programs so you could automatically install them when you get your new system up. I'm no expert on the package manager though =(

---

### Post by michaelpagz on 2010-10-07
Related question. Will using a wubi install of Ubuntu result in more functionality than a fresh Ubuntu install? 
My situation is that I have a Thinkpad Edge and I was surprised to find that when I installed Ubuntu with wubi everything but trackpoint worked out of the box. Is this because Windows is still "in control" so to speak or is Ubuntu accounting for all of my hotkeys and functionality?

Hope that makes sense
Thanks!

---

### Post by lisati on 2010-10-07
You will need to move your Wubi installation to its own partition. There are a number of threads in the forum which touch on how to do this.

The following links are just two of several (note the warning at the start of the first):
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
[http://ubuntuforums.org/showthread.php?t=1312640](http://ubuntuforums.org/showthread.php?t=1312640)

---

