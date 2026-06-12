---
title: "Format Help"
date: 2010-08-25
forum: General Help
---

### Post by V3N0M036 on 2010-08-25
Hello all and thanks in advance.

I have recently decided to switch from Ubuntu 10.04 LTS to Windows Vista. However I'm encountering a few problems. I cannot get windows to boot from startup like a normal Format/Install I've done in the past. Through research I'm assuming this is because of partitions. If you could help me correct the settings that would be awesome.

My machine:
Hp Pavilion
64 bit
4gb ram
300gb hardrive 

I can of course give any info if you need. I'm a Ubuntu newbie so please explain in depth, My main goal is a clean format and install. :D

---

### Post by Bucky Ball on 2010-08-25
You are setting the machine to boot from the cd in the BIOS? Silly question but you never know. Don't know that Windows is going to recognise EXT partitions though. Best; put in a Ubuntu Live CD (install cd), run the demo, go to Gparted (System->Partition Editor), unmount all the partitions and erase them.
Done.

---

### Post by V3N0M036 on 2010-08-25
Yeah I've tried booting on the bios from CD and USB stick. The computer simply ignores it and continues to boot ubuntu normally. After Erasing the partitions The installation should happen as usual correct?

---

### Post by Bucky Ball on 2010-08-25
If you remove Ubuntu and erase the disk there won't be anything to boot from. That much I know. But strange you are not able to boot from the CD. BIOS, Boot, Boot order, Optical drive at the top of the list or marked as boot device?

---

### Post by V3N0M036 on 2010-08-25
Yeah changed the boot order so they come first. could be the c.d.?

---

### Post by Bucky Ball on 2010-08-25
Yea, could be. Generally though it will still try to boot from it and give a message like 'no operating system found.' I would perhaps try another CD though or see if the one you have boots on another machine. If it does, might be the optical drive. To test that try another CD (audio or whatever).

---

### Post by Mark Phelps on 2010-08-26
First of all, from what I recall, Vista came on a DVD, not a CD.  So, if you truly have a CD, there may be problems with it.

Second, can you boot from other CDs, just not Vista? If so, download and burn a GParted LiveCD (which you can get from distrowatch.com) and use that to remove the Linux partitions.

---

### Post by Bucky Ball on 2010-08-28
> **Mark Phelps said:**
> First of all, from what I recall, Vista came on a DVD, not a CD.  So, if you truly have a CD, there may be problems with it.

Second, can you boot from other CDs, just not Vista? If so, download and burn a GParted LiveCD (which you can get from distrowatch.com) and use that to remove the Linux partitions.

OP said CD and thanks for reiterating everything I've already said. Maybe you should read previous posts. ;)

---

### Post by JBAlaska on 2010-08-28
Why in the world would anyone want a blind dog?....erm I mean Vista. Vista is the windows ME of the 21st century. Get a copy of windows 7 and save yourself some grief.

---

### Post by Bucky Ball on 2010-08-29
> **JBAlaska said:**
> Why in the world would anyone want a blind dog?....erm I mean Vista. Vista is the windows ME of the 21st century. Get a copy of windows 7 and save yourself some grief.

+1. Or XP.

---

