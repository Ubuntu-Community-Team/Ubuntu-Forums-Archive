---
title: "Help needed:  Creating LiveCD/New install"
date: 2011-10-26
forum: General Help
---

### Post by milamdobbins on 2011-10-26
Hi all, I'm not sure if this is the right forum, but here goes nothing.

I've got a lot of programs/customizations on an Ubuntu machine that I want to copy over to about 40 sites that are all running windows at the moment.  Everything was going okay until the new update came out to 11.10, and I decided what the heck and upgraded. That caused a lot of problems, but I got it all worked out.


What I need help with is to get my system into a live cd format.  I tried Remastersys and a couple of other programs like it, and they didn't work.  My system would freeze, and the few DVD's I got wouldn't boot anything.  I also tried going through the routine at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization), but any time I try to switch out a folder or try to add something, the livecd won't get past trying to load.

I can get the LiveCD tutorial to work, but only if I don't modify anything, which is pretty useless to my purposes.  Can you guys point me to a tutorial or software that I might have missed, that definitely works with 11.10?  Thanks in advance!

---

### Post by jamesisin on 2011-10-26
I know you can make disc images using dd (that's a command line utility).  You could certainly image your current machine to an external hard drive using dd.  I suppose you could potentially create a CD using it.

---

### Post by elliotn on 2011-10-26
have u tried re-linux? I haven't used it myself but I heard it a remastersys fork and its better

---

### Post by metalf8801 on 2011-10-26
I know this isn't what your looking for but you could use Clonzilla or another program on the free open source live CD Parted Magic (not to be confused with the tool Norton makes) to make a bit for bit copy of your existing system. 

[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php) 


There is some documentation on making a customized Live CD here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Sorry I can't help more
Dan

---

### Post by milamdobbins on 2011-10-26
Thanks for the replies!

I think I used DD in one of my attempts, but I'll give it another go.  Looking at parted magic now.

Here goes nothing, eh?  Whenever I solve this, I'm going to post a tutorial on it somewhere for sure.

---

### Post by oldtimer7777 on 2011-10-26
I personally use Relinux for making my own personal dist of Ubuntu.  Right now I tried it on Ubuntu 11.10 and Relinux works perfectly for what you are attempting to do. It is very simple, fast, and reliable too. Here is where you can learn more about how to install it and do what you are attempting to do:

[https://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](https://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)

> **milamdobbins said:**
> Hi all, I'm not sure if this is the right forum, but here goes nothing.

I've got a lot of programs/customizations on an Ubuntu machine that I want to copy over to about 40 sites that are all running windows at the moment.  Everything was going okay until the new update came out to 11.10, and I decided what the heck and upgraded. That caused a lot of problems, but I got it all worked out.


What I need help with is to get my system into a live cd format.  I tried Remastersys and a couple of other programs like it, and they didn't work.  My system would freeze, and the few DVD's I got wouldn't boot anything.  I also tried going through the routine at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization), but any time I try to switch out a folder or try to add something, the livecd won't get past trying to load.

I can get the LiveCD tutorial to work, but only if I don't modify anything, which is pretty useless to my purposes.  Can you guys point me to a tutorial or software that I might have missed, that definitely works with 11.10?  Thanks in advance!

---

