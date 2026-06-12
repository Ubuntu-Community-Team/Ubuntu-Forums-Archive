---
title: "Sh!t, just destroyed my partition. Now what?"
date: 2010-03-10
forum: General Help
---

### Post by CathalG on 2010-03-10
Whilst using **GPARTED** this morning, I accidentally deleted my partition. Now, on booting the machine it returns:

```

GRUB loading.
error: no such partition
grub rescue>

```

If I run **SET** it returns:

```

prefix=(hd0,1)/boot/grub
root=nd0,1

```

Is there an easy way to restore the partition information? 

I have lots of PC and MAcintosh experience, but I am a raw LINUIX rookie. Please be aware of this if you are offering assistance.

I'm running (or rather, was running) 9.10 on a laptop. If I have to redo it all again it isn't the end of the world.

---

### Post by t0p on 2010-03-10
You'll need to use a live CD to run a partition editor to recreate the missing partition.  My personal choice would be gparted on an Ubuntu live CD - you'll find gparted under **System >  Administration > Partition Editor**.

You have to use a live CD because your hard drive needs to be unmounted for the partition editor to work on it.  Plus of course you can't boot Ubuntu from your hard drive with the partition missing!

Good luck!

---

### Post by bumanie on 2010-03-10
Try testdisk live cd from [here]("http://www.cgsecurity.org/wiki/TestDisk"), it is able to restore partitions and partition tables etc. If that doesn't work, a tool like photorec should be able to get most of the data back - you will find photorec on the same site. Make sure you read all the documentation on the testdisk site pertaining to restoring partitions, also this [tutoria]("http://members.iinet.net.au/~herman546/p21.html")l may be of help.

---

### Post by CathalG on 2010-03-10
Thanks for the information guys!

I've got my live CD and can boot the machine from that. Probably the easiest thing for me to do is just re-install. I don't keep any real data (perhaps one or two documents that are backed up anyway) on the laptop.

What I was trying to do was make a dual-boot laptop. It's been a dedicated Ubuntu system since Christmas, but there are a few Windows based applications that I wanted to run.

I think I'll revert to XP, and make that dual bootable, and put Ubuntu on second. I think I know what I'm doing that way!

Cathal

---

### Post by bumanie on 2010-03-10
Certainly, installing windows first is always best. Depending on what programs you wish to run from windows, [WINE]("http://www.winehq.org/") may help - many, but not all .exe will run in WINE.

---

### Post by audiomick on 2010-03-10
If you can re-install without any losses, that sounds like a good plan, particularly the bit about installing windows first. It is much easier that way.

---

### Post by ajgreeny on 2010-03-10
Or try VirtualBox direct from Sun to run windows as a virtual machine.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by zaphod777 on 2010-03-10
You can also run virtual box inside Ubuntu that way you don't need to reboot. I don't really like to reboot much. Then it is also easy to share files between the two.

---

### Post by Roasted on 2010-03-10
> **bumanie said:**
> Try testdisk live cd from [here]("http://www.cgsecurity.org/wiki/TestDisk"), it is able to restore partitions and partition tables etc. If that doesn't work, a tool like photorec should be able to get most of the data back - you will find photorec on the same site. Make sure you read all the documentation on the testdisk site pertaining to restoring partitions, also this [tutoria]("http://members.iinet.net.au/~herman546/p21.html")l may be of help.

Serious +1 to TestDisk.

I was in disk management within my XP partition and deleted my Ubuntu partition accidentally. This also wiped out my ability to boot up XP again since Grub was then gone since it resided on Ubuntu's side.

I never had used TestDisk before, but I got it figured out and literally within two minutes.

---

