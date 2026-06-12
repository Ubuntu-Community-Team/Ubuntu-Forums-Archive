---
title: "Install alongside other OS destroyed Windows"
date: 2010-12-27
forum: General Help
---

### Post by rbanavara on 2010-12-27
My friend installed Linux Mint on his DELL laptop with windows 7. He chose the option "Install alongside other OS" option to install Mint. Now He does nor have option to boot Windows (as this over wrote his Windows). I asked him to try running fdisk -l and it shows only linux partion, extended partition & swap.

I will be asking to try recovering data with testdisk.

I have few questions:

1. If the installer says "install alongside other OS" why it overwrote Windows (or did he make any mistake). The intention here is to understand is this a human error or issue with installer, so that this can be properly addressed. I never used this option so I am not sure how this works (probably I am skeptic and always use gparted to partition)

2. What are the chances of recovering the files. Are there any better alternatives than using testdisk.

---

### Post by garvinrick4 on 2010-12-27
I have found their are quite a few times when users say linux installer screwed up my
computer you are not getting full story. The installers do what you tell them to do!! So
you just have to try and help the person as much as possible and not worry about
did the linux do it or did the user do it. There are some users in this forum who have 
mentioned recovery tools and will hopefully chime in and help you. Good luck with your buddy.

---

### Post by coffeecat on 2010-12-27
Hi - you can assure your friend that this is not human error. This is a design problem in the install alongside option in the installer. You can read more - much more - here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Sorry I can't help with the rest - need to log off soon - but there will be others along with experience of this issue.

---

### Post by Quackers on 2010-12-27
I will add your name to the Ubiquity Hall of Shame. Sadly!

---

### Post by garvinrick4 on 2010-12-27
# Is Mint using Ubiquity?
# Edit: Looking at Mint and it has been using Ubiquity longer than Ubuntu.
# Looks very interesting never tested it will have to load one and see what it does.

---

### Post by rbanavara on 2010-12-29
_Update:_
Could successfully recover the data with testdisk. I gave gim partedmagic disk and told how to use testdisk. He could recover data.

The installer had created one big ext4 root partition and a logical swap partition of 18Gb!!!

Just wondering what would have caused this. Dell normally has 3 partitions, utility, recovery & OS. Probably the installer failed to correctly identify OS partition (since there were other partitions). Have not read the post referenced in the above threads. Will post back when I go through that.

---

