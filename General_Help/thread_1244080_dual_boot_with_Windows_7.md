---
title: "dual boot with Windows 7"
date: 2009-08-19
forum: General Help
---

### Post by alonsh4 on 2009-08-19
hi every1,

i'm a new linux user, and i've been reading these forums for quite some time now. it's pretty resourceful around here :KS
until now i managed to find answers to the questions i had, but now i'm posting my first question, since i can't seem to find the answer. btw, i'm not sure this is the right place to post this question, so feel free to move this thread to it's rightful place.

atm, i'm using both XP and Ubuntu on my home pc. i've been using XP for years now, and i recently installed Ubuntu on another partition. after the install, a Dual Boot screen was automaticly created ofc, and now i can choose which operating system to load.

now, let's say i want to install Windows 7 instead of XP. i'm guessing that if i just format my XP partition and install Win7 then the dual boot screen will be kinda broken, and still have the XP option in it, which probably will not work. 

so, did any1 try anything similar? what's the right way to install a different Windows and change the dual boot screen with Ubuntu accordingly?

i'd appreciate the advice :)
thanks

---

### Post by forgotten_hell on 2009-08-19
I'm new at Ubuntu myself and tend to know more about Windows, but I think this question is general enough I could answer it. 

As far as I know, the partition should keep everything completely separate. Therefore, when you reformat the Windows partition and install Windows 7, everything should still work. I don't think it would affect anything negatively. Unless you're asking something else...

---

### Post by Barafu Albino Cheetah on 2009-08-19
The only problem with dual boot is bootloader. When windows is installed it searches and destroys linux bootloader called grub. Grub can load windows too, but windows intentionally will not load linux. There is a LOT of how-tos on the problem, read them. 
 My good advice:
[LIST=1]
[*]Learn a bit about grub configuration.
[*]Create a removable holder for bootloader: floppy or USB stick.
[*]Keep it updated: reinstall bootloader every time you change kernel.
[*]Remove the medium while installing any OS.
[*]Now you are always protected against any bootloader problems. You can boot from that medium and reinstall grub.
[/LIST]

---

### Post by ithinkitschad on 2009-08-19
noooooo. The install will overwrite your grub bootloader. Its cool though g. Dont worry all you have to do after is boot into the ubuntu live cd and recover grub. Its really not hard, I've done it, so chances are you can handle it too. There might be an even easier way. Heres the [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to the instructions. But you should research it first, maybe theres an easier way. Good luck.

---

### Post by alonsh4 on 2009-08-19
thanks for the quick reply guys!
i'm currently at work, but when i come home tonight i'll try those things. seems to me that simply installing Win7 on the XP partition and then use the Ubuntu boot CD to recover the grub will do the trick.

---

### Post by vikramk.ibs on 2009-08-19
> **ithinkitschad said:**
> noooooo. The install will overwrite your grub bootloader. Its cool though g. Dont worry all you have to do after is boot into the ubuntu live cd and recover grub. Its really not hard, I've done it, so chances are you can handle it too. There might be an even easier way. Heres the [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to the instructions. But you should research it first, maybe theres an easier way. Good luck.

Thanks for the recovery tutorial its really helpful.

But after recovering the Ubuntu GRUB. If my OS is different

initially it was XP SP3
now it will be Win7

Will it make any problem??

---

### Post by Barafu Albino Cheetah on 2009-08-19
look into /boot/grub/menu.lst You will see Windows version means nothing to grub.

---

### Post by ithinkitschad on 2009-08-19
> **Barafu Albino Cheetah said:**
> look into /boot/grub/menu.lst You will see Windows version means nothing to grub.

Yeah you can make it say "windows is a pretty stupid operating system for people without patience to learn"

---

### Post by automaton26 on 2009-08-19
Before changing any boot stuff, I'd always advise that you back-up all your files and data first, _and_ verify they have been saved correctly.

Then, if you don't want to do any grub work, you could use this process instead:

1) Install Windows 7 first - during the install, remove all existing partitions and create one single partition (NTFS).
2) Install Ubuntu last - during the install, repartition and create a separate 2nd partition (ext3 or ext4).
3) Restore your data from the back-up.

You'll then have to reconfigure both systems, and restore all applications of course, but some less technical users still find that process less daunting.

Let us know if it goes OK :)

---

