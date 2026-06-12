---
title: "Failure to boot windows"
date: 2010-01-14
forum: General Help
---

### Post by TehBleachBottle on 2010-01-14
I've had problems getting Windows to boot ever since I reinstalled it and then reinstalled the grub boot loader. Normally one would think that I would get a Error * message or something along that line but it starts with a quick flash of some text that says "Starting.." and other stuff I can't read before it disappears. Then it goes to my computers built in diagnostic tool, which obviously won't help since it isn't a real hardware problem either.

I ran fdisk and here are some odd things that came up.

> The number of cylinders for this disk is set to 5222.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Partition 3 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 3.
Total allocated sectors 3736423994 greater than the maximum 83891430


Windows is located on /dev/sda2 by the way.

---

### Post by Sef on 2010-01-14
What version of Ubuntu are you using?

---

### Post by TehBleachBottle on 2010-01-14
I'm currently using Ubuntu 9.10 64-bit. 

I ran gParted just to check the partition and after saying that i should run chkdsk /f I checked the partition. Gave me an error and I was in the process of saving it when it froze and I had to force quit. I'll give you the details for the error in a bit.

---

### Post by TehBleachBottle on 2010-01-14
> GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Check and repair file system (ntfs) on /dev/sda2  00:00:26    ( ERROR )
     	
calibrate /dev/sda2  00:00:01    ( SUCCESS )
     	
path: /dev/sda2
start: 80325
end: 83971754
size: 83891430 (40.00 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:25    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda2

Though that doesn't seem very helpful...

---

### Post by Sef on 2010-01-16
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Download").  It has [fixed]("http://ubuntuforums.org/archive/index.php/t-260315.html") your problem before.

---

### Post by TehBleachBottle on 2010-01-17
I fiddled around with it a bit but I don't quite get what I need to do to fix it using Testdisk.

---

### Post by mhgsys on 2010-01-17
@TehBleachBottle

ahum; This might be quite helpful 

[http://lmgtfy.com/?q=howto+testdisk](http://lmgtfy.com/?q=howto+testdisk)

---

### Post by Leppie on 2010-01-17
> **mhgsys said:**
> @TehBleachBottle

ahum; This might be quite helpful 

[http://lmgtfy.com/?q=howto+testdisk](http://lmgtfy.com/?q=howto+testdisk)
not only for TechBleachBottle... lol

---

### Post by TehBleachBottle on 2010-01-19
Thanks that did the trick.

---

