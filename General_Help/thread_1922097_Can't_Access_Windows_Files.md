---
title: "Can't Access Windows Files"
date: 2012-02-08
forum: General Help
---

### Post by Bill Gates Foundation on 2012-02-08
fixed: thanks post #4

I installed XP. 

Then, I installed ubuntu 11.10 inside windows, with 30gig.

The problem is, while in ubuntu, i can only see the 30gig it let me partition, where is the rest of my 110 gig hard drive?????

gpartition did not work......
ntfs-3g did not work......


fixed.......thanks post #4

:guitar:

---

### Post by Quarkrad on 2012-02-08
I've only use Virtualbox - not sure what you are using to run Ubuntu in Windoze.  In the **Settings** part of Virtualbox for the guest machine (Ubuntu in your case) there is an option to **share folders** - once this is set up you can access your Windoze folders from Ubuntu.

---

### Post by Quarkrad on 2012-02-08
In my experience it is much better to create a small partition on your HD and run Ubuntu natively.  You can then dual boot to either OS.

---

### Post by jamesisin on 2012-02-08
If this is a Wubi installation you ought to be able to access your C drive where it is mounted at /host in your Ubuntu system.

---

