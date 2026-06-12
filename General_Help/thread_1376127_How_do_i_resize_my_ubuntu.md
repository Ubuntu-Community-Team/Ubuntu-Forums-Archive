---
title: "How do i resize my ubuntu ?"
date: 2010-01-08
forum: General Help
---

### Post by AkhlD on 2010-01-08
hello im new to ubuntu..i have installed ubuntu on a 12GB partition.now i need to expand the partition i tried with Gparted.but cant Fix..please help me out...
[IMG]http://img190.imageshack.us/img190/7342/screenshot1ej.png[/IMG]

---

### Post by tom.swartz07 on 2010-01-08
Hi.

Id be more than glad to help you, I just need a bit more info about your system.

What are all of those partitions you have there? What do you have on SDA1-7?

If one of those are not needed, we could resize (or remove) one of those partitions and expand your Ubuntu partition.

As it stands right now, you cant- you dont have any room. Its really easy to do once you clean things up a bit though.

You will need a LiveCD to perform the move too. Download an Ubuntu .iso the same version as you are using (9.10 it looks like) and burn it to a disk at a slow speed.

---

### Post by mkvnmtr on 2010-01-08
First thing that looks like you have gparted running in your Ubuntu system. It will not work on a mounted partition. You need to either boot from a Ubuntu live disk and use gparted from there or use the gparted live disk. 
Then it will not be hard to give yourself more room.
Right all the things you want to do are greyed out but when you boot from a live disk you can unmount the partitions and work on them.

---

