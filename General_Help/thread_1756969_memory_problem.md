---
title: "memory problem"
date: 2011-05-12
forum: General Help
---

### Post by ChinaManLiu808 on 2011-05-12
hey i created a 26 gig partition for ubuntu but in my home folder it says a only have like 83 mb of free space. so i can't really add music or anything to my computer. please help thanks.
sony vaio p series. 60 gig hard drrive. ubuntu 11.04

---

### Post by jerrrys on 2011-05-12
doesn't sound right.  are you getting a warning about disk space when you boot up?

if not open a terminal and enter the command **df** and see what that says.

---

### Post by ChinaManLiu808 on 2011-05-13
yeah ii get that message some times and theres nothing for me to delete. 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             2765720   2482980    142248  95% /
none                   1018292       672   1017620   1% /dev
none                   1024896       276   1024620   1% /dev/shm
none                   1024896       104   1024792   1% /var/run
none                   1024896         0   1024896   0% /var/lock
/dev/sda3             25110524   3863868  21246656  16% /host
but thats what it says

---

### Post by jerrrys on 2011-05-13
yep, you used it up.

download **bleachbit** if you can and follow the instructions and run it

if your lucky,that will free up one or two gig

its in the software center

---

### Post by tink2520 on 2011-05-14
> **jerrrys said:**
> yep, you used it up.

download **bleachbit** if you can and follow the instructions and run it

if your lucky,that will free up one or two gig

its in the software center
I've used bleachbit 3 times now, as root, and it fails to remove much of anything, even after 20 minutes of waiting.  It also seems that every time I delete anything More memory gets used.  My cpu is a consistant 100% for both.  What else can I do?

---

### Post by jerrrys on 2011-05-14
ok, those warnings were there for a reason.  some actions take a loooong time.  no sudo this time.  open bleachbit as user and just check everything that does not give you a warning box. once is enough

---

### Post by tink2520 on 2011-05-15
Oh I most definitely heed those warnings and only used sudo the last go round.  I've learned my lesson about not erring on the conservative side.  I think my real problem is a faulty hard drive that is spamming itself to an early grave.  It seems it wasn't just bleachbit having erratic  responses but any program, default or otherwise, seemed to have the same issues.  Some confirmed deletion while the packages were obviously still there and others just gave up while issuing odd warnings about a random circumstance.  
I was using these programs to try and extend what little life she has left but it seems a replacement is needed asap.  I want to back up all my configurations and programs and recently tried backintime and it seemed t be doing well until the end when it only saved partials of some files and zero for others.  And my memory is filling up faster than I can delete (maybe delete) them.  And with the cpu at 100% almost consistently it is hard to accomplish even the most mundane tasks.  I will be receiving a new dell laptop within a few weeks and I want to have an exact replica of my current  laptop.  What can I do to quickly free upor add to my memory so I can get everything I need before it finally self destructs?  
I seem to behaving difficulty compressing files as well, so it makes it hard to transfer to a usb or cd.  I also dont have a live cd  because it was an install from a friend, who as it figures, is currently unavailable to solve all these issues for me.  Any suggestions would be much appreciated and would keep me from helping her into an earlier demise.

---

### Post by tink2520 on 2011-05-15
ALso it seems that xorg seems to be running away with itself which seems to be a big part of the memory issue as well as speed.  2nd runner up is gnome..I think they are having a race because if its nt one its the other.

---

### Post by jerrrys on 2011-05-15
wow, forget bleachbit.  can you get someone to burn you a cd ?  

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

i guess worst case would be to take it to a shop

EDIT some one with a high speed internet

---

