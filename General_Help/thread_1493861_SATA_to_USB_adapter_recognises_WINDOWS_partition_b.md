---
title: "SATA to USB adapter recognises WINDOWS partition but NOT LINUX partition, on HD"
date: 2010-05-26
forum: General Help
---

### Post by craig_gonah on 2010-05-26
Hi
This is my first post here but have searched for several days before doing so, but couldnt find anything to help.

Afew weeks ago my Latop died. A GRUB file has become corrupt so it would no longer Boot Linux..tried several fixes involving the GRUB Boot Loader but nothing worked, decided I need to reinstall Linux.
Decided to first grab all the files off the HDD.

The HDD has 2 partiiton..1 Windows Vista and 1 Linux Ubuntu

I have an 'IDE/SATA to USB adapter' which I can plug into a spare Windows machine I have. When I do this it opens the HDD with the Windows files on it, but my Linux Partition can't be found.
I have tried connecting it to a Linux machine and again all I can access is the Windows partitions data.
I have tried connecting it to a Linux machine and booting it so that the external HD is the Primary HD. But no luck. 
The HDD is 110GB in total.

I am very worried that my code is lost..even though logic tells me it must be on the HDD somewhere...

When I run fdisk this is what I get (on a Linux Ubuntu machine with my HDD connected) :

#fdisk -l

---------- prints the below --------------
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11          34      192780   83  Linux
/dev/sda3              35       19452   155975085    5  Extended
/dev/sda5              35        4897    39062016   83  Linux
/dev/sda6            4898        5262     2931831   82  Linux swap / Solaris
/dev/sda7            5263       19452   113981143+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03a49caf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9764864   27  Unknown
/dev/sdb2   *        1216       14594   107453440    7  HPFS/NTFS
---------- ends here ------------

All I wish to do is access the Linux code/partition on my HDD as there was quite alot which wasnt backed up (very stupid...lesson learned believe me)..

Any help would be GREATLY appreciated as am desperate for it..

thanks

Craig

---

### Post by dino99 on 2010-05-26
here is an example to show you how to chroot from outside (a live cd or else)

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

which release are you running ? which grub (1 or 2) ?

when you says: my pc died, what you really mean ? what model of adaptator is it ?

its good to have an external tool on which you can boot then fix: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by craig_gonah on 2010-05-26
Hi
thanks for a speedy response.

By it died, i mean that it throws the below problem when I try and boot my Linux Partition

'GRUB4DOS Memory:638K/1013M MenuEnd:0x4352E
[Minimal BASH-like line editing is supported] '

Then there is a GRUB terminal where I can type commands understood by the GRUB.
I have read instructions to fix it but none have worked.

I am going to burn PartedMagic to CD and run my machine with the HDD back inside and tell it to boot by CD.

I tried mounting the external source and chroot from outside, but the contents of the external HDD remain ONLY contents from my Windows partition. I have tried it for sdb1 and sdb2 but sdb2 with neither showing any signs of my old Linux layout.

Will let you know after I try the PartedMagic.
thanks

---

### Post by dino99 on 2010-05-26
grub4dos ?

why that choice ?

---

### Post by craig_gonah on 2010-05-26
Not something I chose...bought the laptop several years ago...about a year and half ago installed Linux Ubuntu as a partition.
That error message was the first I had heard of 'GRUB4DOS'.

Im abit stumped as to how somebody normally gets data off a Linux Partitioned HDD.

Im really hoping the PartedMagic program works as im out of ideas if it doesnt.

Is there anything else I can try in order to connect a machine to the Linux partition on the HDD?
thanks

---

### Post by oldfred on 2010-05-26
I have not used teskdisk but many have had good luck with it. In finding or repairing missing partitions or files.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by craig_gonah on 2010-05-27
Hi
This has gone very wrong.
Used TestDisk to analyse it and and it found three Partitions on the HDD, none of which were my Linux partition.
Took the HDD home to download PartedMagic on the Windows partition and burn it onto CD, but now my machine will not turn on (even with the HDD inserted again).

I had taken it out and put it back several times before runnng TestDisk and had no problems.
I do not think TestDisk has caused the issue but I can't be sure. It sounds like a physical issue as now the machine will not turn on at all. It should at least turn on...

Do you think I should call it a day and take it into a shop (really dont want to)?
thanks

---

### Post by jerrrys on 2010-05-27
by not turning on, do you mean no lights, no screen, no nothing?

---

### Post by craig_gonah on 2010-05-27
Yep, no sign of life at all.

---

### Post by craig_gonah on 2010-05-27
I suppose its possible an Electrostatic Discharge has killed it...

---

### Post by jerrrys on 2010-05-27
whats the make and model?

---

### Post by craig_gonah on 2010-05-27
Its a Sony Vaio.
Can grab the model number when I get home later.

---

### Post by jerrrys on 2010-05-27
ok

---

