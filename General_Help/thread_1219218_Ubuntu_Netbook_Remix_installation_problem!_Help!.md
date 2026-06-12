---
title: "Ubuntu Netbook Remix installation problem! Help!"
date: 2009-07-21
forum: General Help
---

### Post by saggitheman on 2009-07-21
[COLOR="Red"]NOTE: Not important!

Symboles:

-   |---------------|^|  <---That is a click window. click the arrow and it comes down a list of options.
- # <---That is a square that you can press. you can choose,if you know what i'm talking about
- Text marked with [COLOR="Lime"]Green[/COLOR] is the messages the computer says. 
-Places marked with -------- means that it's blank.
[/COLOR]
Hi.

I'm trying to install UNR 9.04 on my Packard Bell Dot Netbook pc
who i bought yesterday...
But it has two partitions! one named: OS and another named DATA.
The OS partition is the one with the Windows on! And i wan't to keep my Windows! The DATA partition is empty when i open it in Windows, but when i open it on the UNR liveCD /USB! It has two folders named RECYCLER and System Volume Information.

In The System Volume Information folder i find a folder named EfaData and another one named _restore(and-many-numbers)

In the RECYCLER folder i find another folder with a file named Desktop.ini.

Okey. 
-I want to keep my Windows
-When i'v come to the part to set my Keyboard language, i set my selection and press Forward.
-Then it comes up a window that says:

[COLOR="Lime"]The installer has detected that the following disks have mounted partitions

/dev/sda

Do yo want the installer to try to unmount the partitions on these disks befor continuing? If you leave them mounthed, yo will not be able to create, delete, or resize partitions on these disks, but you may be able to install existing partitions there.

[/COLOR]-Then i press Yes
-Then i choose "Specify partitions manually(advanced)"

I have these partitions

[COLOR="Lime"]
Device----|Type-|Mount point|Format?|Size-----|Used
/dev/sda---|-----|-----------|--------|-------------|
-/dev/sda1|ntfs-|-----------|---#---|8589 MB--|6577 MB
-/dev/sda2|ntfs-|-----------|---#---|55720 MB-|12894 MB
-/dev/sda3|ntfs-|-----------|---#---|55721 MB-|Unknown[/COLOR]

The sda1 says Windows Vista Loader.
The sda2 is the Windows XP partition (Keep that).
The sda3 is the Data Partition... Don't know what this is! You Know?

Anyone know how to install Ubuntu Netbook Remix 9.04?
I select the sda3 and press "edit partition"  

Then it says.

Edit a partition
[COLOR="Lime"]Use as:----------------|do not use the partiton|^|

Formate the partition: #

Mount Point:----------|-----------------------|^|[/COLOR]


So how can i install the UNR? can i delete the sda3 partition? and make root, swap, partition?

BTW, i'm no noob, that's not the reason i'm typing to much!
I just want you to see what i'm acctually talking about.

Please help me to install UNR to my PB Dot (NC15) Netbook!

---

### Post by mikewhatever on 2009-07-21
I think it's enough to resize sda3, in other words, shrink it, thus freeing about 20 Gb of space, and create the Ubuntu partitions.
Check out the installation guide too [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

---

### Post by saggitheman on 2009-07-21
That was the problem... I couldn't shrink it because it was there by default. so i edited the partition in windows. and worked!

---

