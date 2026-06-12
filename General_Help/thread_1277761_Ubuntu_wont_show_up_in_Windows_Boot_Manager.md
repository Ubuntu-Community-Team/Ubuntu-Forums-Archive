---
title: "Ubuntu wont show up in Windows Boot Manager"
date: 2009-09-28
forum: General Help
---

### Post by xxhopingtearsxx on 2009-09-28
I just installed Ubuntu with Wubi (it wont let me boot from the CD for some reason, and Wubi is much easier) and when I rebooted my PC after installing, Ubuntu doesn't show up. I don't know how to get to it..

I want to use Windows Boot Manager, not Grub. I'm not all that much familliar with Grub. Please help. I've made threads and haven't gotten much help and I only seem to get one answer and then the thread dies (no matter how many times I bump, it goes down to the next page). Is this really a thing no one can fix? I hate Windows, I was just getting to enjoy Ubuntu before I uninstalled it (I had some wifi problems and thought reinstalling would help but thats another story) and now I can't even get back to it. I want to get back on Ubuntu.

---

### Post by rcayea on 2009-09-28
I believe if you download the SuperGrubDisj iso and burn and boot from it there is an option fairly early on in the disk setup to let you repair windows with linux listed. 

check the SGD website.

---

### Post by xxhopingtearsxx on 2009-09-28
I don't know how to do that. :[

---

### Post by Darkwing-Duck on 2009-09-28
Okay, the problem is that windows bootloader doesn't like to play with others very well. You will need to restore grub to get it to run the right way. 

So, GRUB is going to work for you. Since you cannot boot from CD try making a bootable USB thumb drive. You can find the directions here. 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Okay, use that to boot into a liveCD and restore to allow for dual boot. Here are some directions to restore grub.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

