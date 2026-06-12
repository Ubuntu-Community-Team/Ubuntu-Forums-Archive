---
title: "Huge problem (unallocated partition)"
date: 2010-12-28
forum: General Help
---

### Post by Ductape on 2010-12-28
My main goal was to reinstall windows vista home basic
 
Ok so i was on my way to making my partition a FAT so i made it unallocated so i can do the process. my computer suddenly shut off. now it wont start back up heres my plan.
 
go to my girlfriends house
download the ubuntu live CD into a usb or cdr/dvdr
load up using that
Making my original harddrive a FAT32 so i can install windows vista
 
 
would this work or is there other way i can save my laptop from becomin poop?

---

### Post by mikewhatever on 2010-12-28
So, are you saying that to install Windows Vista, you need a pre=formatted FAT32 partition? That's new to me. Windows should be able to create its own partitions during the installation.

PS: Since when unallocated partitions became a huge problem?

---

### Post by Ductape on 2010-12-28
ok heres the whole thing
 
first i burned windows vista home basic (because my this was my laptops original OS)
tryed to boot it but ubuntu wouldnt recognize it when starting up even tho i set the boot to cd/dvd. so i looked up why and i saw a post saying that the install disk doesnt recognize linux's ext partition format so i looked further into it and started doing what it said. i went into gparted and unallocated my partition. then i started making my partition 2 fat32 formats.(because thats how it was originall) then i got busy talking to people on aim and facebook so i didnt actually tell gparted to do the operation. Then my battery got real low so i hiberated so i can find an outlet. i found an outlet and turned on my laptop and it went to a blank screen with a blinking line. 
 
so again my plan was to 
 
get a live cd usb 
reformat the partition 
reinstall ubuntu or get vista to work....
 
would this work or is there any other options i can go about this.
 
im also going to try installing windows froma usb or something ergh i hope i can get this to work

---

### Post by Deer Hunter on 2010-12-28
To my knowledge you don't have to format the hard disk as FAT32 to install Vista; the installer should be able to format the disk to the proper format.  BTW, it's news to me that Vista uses the FAT32 format; I thought Windows had been using NTFS for several distros now.

Anyway yes, get the live CD, go into GParted and delete the partitions; then boot back into the Vista installer, which should be able to make it's own partition.  I said "partition," singular, because I don't see why Vista would need two.  It might have had a recovery partition, but I'm assuming you don't have the recovery disks or else you would've tried ithem.  Anyhow, If that doesn't work, go back to Gparted and make a NTFS partition on the whole hard disk, and see how it goes to install Vista that way.  At any rate, let us know how it goes.

Best wishes

Deer Hunter

---

### Post by mikewhatever on 2010-12-28
Your disk is now unallocated, so there is no Linux file system there, right? Just Install Vista and stop making things complicated.
You'll probably also get much better help on a Vista forum.

---

### Post by Mark Phelps on 2010-12-29
Vista doesn't use FAT32 for its OS partition; it uses NTFS -- and a newer version of NTFS than was present in Windows XP.

You would do better letting it do its own partition formatting.  That way, it will be the correct version of NTFS.

---

