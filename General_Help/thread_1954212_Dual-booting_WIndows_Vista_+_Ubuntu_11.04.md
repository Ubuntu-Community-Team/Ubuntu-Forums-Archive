---
title: "Dual-booting WIndows Vista + Ubuntu 11.04"
date: 2012-04-07
forum: General Help
---

### Post by Ge689 on 2012-04-07
Hi guys, fairly inexperienced user here:
 
I'm looking for some help as to whether I can dual-boot Windows Vista alongside Ubuntu 11.04 which I know is possible and fairly simple to do, but my problem is that all of my Vista files are on an external hard-drive and my laptops hard-drive is 100% Linux.

Is there any way to add the files/partition/do something, that will allow me to dual-boot Vista and Ubuntu, or replace it entirely if need be?

Any help would be greatly appreciated :)
Thanks :)

-Ge689

---

### Post by CottonCandy on 2012-04-07
So Vista is on the external hard drive & Ubuntu is on the laptop hard drive? Are you trying to dual boot with both hard drives or put both OSs on one hard drive?

---

### Post by Mark Phelps on 2012-04-07
If you boot from an Ubuntu CD, you can use the Gnome Partition Editor (known as GParted) to shrink the Linux filesystem partition and make soom room.

Then, when you boot from the Vista install DVD, you can install it to the unallocated space.  It will automatically partition that for you.

---

### Post by Ge689 on 2012-04-07
Trying to get both OS's onto the single laptop hard-drive.

The thing that is most likely gonna be a problem is that I don't have a vista cd, the laptop came with it pre-installed and no disc.

---

### Post by CottonCandy on 2012-04-07
Where is Vista installed? Is it on the laptop or the external drive?

Because 
> **Ge689 said:**
> my problem is that all of my Vista files are on an  external hard-drive and my laptops hard-drive is 100% Linux.
and
> **Ge689 said:**
> I don't have a vista cd, the laptop came with it pre-installed
say two different things to me.

---

### Post by Ge689 on 2012-04-07
The laptop had Vista installed with no disc, but I took all the Windows files and put them on the external hard-drive then installed Ubuntu and made that the main OS on the laptop, no other partitions or anything.

---

### Post by holycow131415 on 2012-04-07
If you have a valid CD key on the laptop, you can then download legally the ISO of Vista.

---

### Post by Ge689 on 2012-04-07
> **holycow131415 said:**
> If you have a valid CD key on the laptop, you can then download legally the ISO of Vista.

Where would I find a legitimate source for the ISO? The Windows website states they don't sell it anymore but continue to support it?

---

### Post by CottonCandy on 2012-04-07
You may want to try editing your thread title to say "Help getting Vista install CD or .iso" or "Installed Ubuntu on entire drive, now want to dual-boot but don't have Vista install disk".

---

### Post by holycow131415 on 2012-04-07
Sorry, they used to be free on neosmart but no longer are. Your best bet would be to torrent it. Make sure you download the correct version, OEM(hp, tosihba, dell, etc). Or call the manufactuer to get the disk (prob need to pay something for that).

Also, if you still have OEM backup software installed, just create the disk yourself ;)

---

### Post by Ge689 on 2012-04-07
Okay, I've searched through everything and there's quite a lot of files relating to OEM, what is it specifically I need to create the disk myself?

(Sorry for so many questions by the way, not the most knowledgeable in this area)

---

### Post by holycow131415 on 2012-04-07
It would probably be in the form of an ISO file, so use imagburn to burn it on to a cd/dvd

---

### Post by Ge689 on 2012-04-10
I downloaded a 32-bit Vista ISO and burned it to a CD, but it won't open, I can access the files on it but it won't auto-run and the setup.exe file won't open with Wine.

---

### Post by Ge689 on 2012-04-12
Okay, I have got the Vista installer open but upon clicking 'Install Now' it comes up with 'Error Code: 0x80004005' saying I don't have enough space for temporary files. 451MB of space is needed on any partition for Vista to install, yet I have more than enough space on this laptop.

---

