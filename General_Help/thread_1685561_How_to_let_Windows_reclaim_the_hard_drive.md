---
title: "How to let Windows reclaim the hard drive?"
date: 2011-02-10
forum: General Help
---

### Post by Dragonbite on 2011-02-10
Don't hate me for doing this, but I have a dual boot Windows XP/Ubuntu machine which I want to remove Ubuntu and set it back to Windows XP.

Mind you, I have 3 hard drives for this laptop and the other 2 are running Linux.  I have reasons to want Windows on one hard drive and I need to give it more space than it has now.

[LIST=1]
[*]What is the easiest way to let Windows XP take over the rest of the hard drive?  I haven't decided if I want to make the former Linux partition in the entire My Documents partition, or make it a single continuous partition.  One method I am thinking of is to boot to a Live Ubuntu session and us GParted to remove & grow the partitions.
[*]How do I remove grub and tell Windows to boot they way it expects to?
[/LIST]

---

### Post by Dragonbite on 2011-02-11
Well I got things backed up for the Ubuntu side so now I can see about taking that whole partition and making it a single NTFS to place the "My Documents" in there.

But I am still not sure how to replace Grub.

---

### Post by marin123 on 2011-02-11
you can boot windows cd into command prompt and do "fixmbr" or "BootRec.exe\fixmbr" to remove grub froma that disk.

be sure to run this without other disks connected to the computer or you can do damage.

---

### Post by mastablasta on 2011-02-11
[QUOTE=Dragonbite]
But I am still not sure how to replace Grub.[/QUOTE]
 
If you want to REPLACE grub with windows you need to use fixmbr command from windows repair/install CD (use the console).
 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by coffeecat on 2011-02-11
If you don't have a Windows install CD, you can use lilo from the Ubuntu live CD to get the mbr to boot Windows without grub. It installs lilo code to the mbr, but this works just as well as Windows code. See this post for the method:

[http://ubuntuforums.org/showpost.php?p=10446990&postcount=3](http://ubuntuforums.org/showpost.php?p=10446990&postcount=3)

That poster also gives a link to supergrubdisc which I've used for this with equal success. You need the legacy super grub disc - I don't know whether the  super grub2 disc has the repair Windows mbr option.

---

