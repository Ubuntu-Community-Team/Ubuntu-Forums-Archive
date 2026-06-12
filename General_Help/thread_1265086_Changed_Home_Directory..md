---
title: "Changed Home Directory."
date: 2009-09-13
forum: General Help
---

### Post by sniper910 on 2009-09-13
well i was screwing around earlier and i managed to change my home directory and now when i go to login it wont let me. i get an error when it loads up and just the cursor on a black screen. anyway to change this back?

---

### Post by harrismh777 on 2009-09-13
When you break the system badly and it won't bootup for some reason, you can try a couple of things....

1) try to boot in the safe mode... and then drop into a root shell... and then fix what ever is broken...   (or)

2) bootup the dvd (or live cd) and drop into a shell.  Mount your home partition (maybe its the same as your root partition), and then fix what you broke, and then reboot.

I am assuming you have some experience with editing with vi ,  or similar tool. If not, find someone who has the experience to help you, either in person, or by phone.   

Don't make things worse by guessing.

---

### Post by rob-ward on 2009-09-13
Before you try to login can you get to the terminal by pressing ctrl + alt + f1

if you can then you will hopefully be able to diagnose and fix the problem much easier. IF you get to the terminal you can grab the output from the following commands, and paste them here

mount

cat /etc/fstab

using that info we should be able to see where your home directory is trying to mount.

---

### Post by sniper910 on 2009-09-13
Well i do believe it is trying to mount in / because that's is where i set it to. didn't exactly realise that would screw me over.

---

