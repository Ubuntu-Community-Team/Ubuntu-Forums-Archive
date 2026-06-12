---
title: "Ext-3 is not supported by Lucid..???"
date: 2010-09-30
forum: General Help
---

### Post by tajiknomi on 2010-09-30
[SIZE=2][I]I am using Lucid, b4 installation i form my partition through Gparted for the first time...,

i have created a **primary disk **as **ext-3 **and give it a space of 45GB,because i want my Ubuntu-lucid to install in that partition,but...

after installation Ubuntu,i see two file-systems!!!...,
the problem here is that Ubuntu has broke my NTFS-partition(here **Data drive**,which was first **50Gb b4 installation**)instead of installing in ext-3 partition, and make **another ext-4 partition by itself**, i don't know y?
i think i have mistake something but i can't recognize my mistake...

moreover,i have created All my **logic Drives as NTFS**,not ext-4 or something else...and My primary partition as Ext-3(45GB)

the pic of my Gparted is attached here with..
[/I][/SIZE]

---

### Post by andrewthomas on 2010-09-30
At some point you did not select:

Advanced/Custom partitioning to tell the installer where you wanted your install to go.

---

### Post by oldfred on 2010-09-30
If you look here you will see the default is to install side by side. It shrinks the windows partition and makes a new ext4 partition and swap in the new free space.

You wanted to check manual to let you choose existing partitions:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by tajiknomi on 2010-10-01
[COLOR=Black][SIZE=2]Thanks to both of you:), actually i recognize my mistake,i have selected SIDE-BY-SIDE option,therefore it shrinks my NTFS and built another Ext-4.

But 1 thing **puzzled** me here is that,my ext-3 drive is completed free,y it shows me that it is **filled approximately 1GB**,and if we look at the Pic,EXT-3 is flagged as "boot".
if Ubuntu is not installed in EXT-3 drive,y it shows the flag "Boot" their???

and i haven't any other OS on my PC....

[/SIZE][/COLOR]

---

### Post by oldfred on 2010-10-01
Journaled file systems allocate some space for the journal, which gparted is showing.

Grub does not use a boot flag (active partition in windows). But some BIOS require a boot flag on a primary partition to let you boot. Lilo & windows use the boot flag to know which partition to jump to to continue booting. Not sure how you got the boot flag, but I would leave it. Perhaps it was there from a windows partition?

---

### Post by turqoisehex on 2010-10-01
If you decide to reinstall, remember to set the mount point of the ext-3 partition as '/'.

Also, it helps to label and set the mount points of all your other partitions at the same time, so they can be automatically included in fstab.

---

### Post by tajiknomi on 2010-10-03
[SIZE=2]*The boot flag is their because i have chosen that as primary..*[/SIZE]

[SIZE=2]thanks to all of u,i got it:P[/SIZE]

---

