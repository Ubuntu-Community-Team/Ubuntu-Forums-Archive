---
title: "Erase Vista and integrate partition in Ubuntu"
date: 2011-03-25
forum: General Help
---

### Post by zandreas on 2011-03-25
Hi all!

I have the following problem. I am running a dual boot system under ubuntu and Vista on my laptop. Many months ago the Windows partition crashed completely so half of my computer is practically dead. 
I would like to erase Vista and integrate their partition in the Ubuntu one. The best case scenario would be if I could just merge the two partitions into one and just have one large Ubuntu partition. If this is not possible, could I create a second hard drive within the linux partition?
I would just erase everything and reformat the whole hard disk to run under Ubuntu, but unfortunately I need my computer on a daily basis for work and I have installed so many programs that it would be really painstaking to reinstall them all from scratch...
I am not so skilled with informatics, and I'm really scared of losing data, so if anyone could spend some time for a step-by-step solution description I'd be really grateful! Or, of course, eventually write a link where the problem is treated.
I am running under Ubuntu 10.04 Lucid Lynx.

Thanks a lot and cheers!!!

---

### Post by Script Warlock on 2011-03-25
you can use gparted to remove the windows partition but don't forget to backup your folders and files and here is the guide [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows). please be careful on editing your grub if you are confused and concerned stop and ask our gurus, who are willing and able to help you...

ps: if you are using the latest ubuntu please refer to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for additional info.

---

### Post by coffeecat on 2011-03-25
@zandreas, the easiest option would be to reformat the Vista partition with either Gparted or Disk Utility and use it as a data partition. You can then either mount it on as-needed basis from the Places menu or the Places sidebar in a Nautilus browser window, or have it mounted permanently on booting up by adding an entry to /etc/fstab. If it's mounted permanently you can then set up symlinks (a bit like Windows shortcuts) to it in your home folder.

You need to format the partition ext3 or ext4. You could format it NTFS but this would be a bad idea if you no longer have Windows to perform a chkdsk on it in case of filesystem corruption. One minor problem with using ext3 or ext4 is that you will run into permissions problems unless you do a couple of things. You either use Disk Utility to format the partition and ensure that the "own filesystem" option is checked. Or you use Gparted and run a couple of simple chown and chmod commands which I can help you with if necessary.

"Merging" the space where the Vista partition is currently with your Ubuntu root partition may be feasible, depending on your partition layout, but involves resizing your Ubuntu partition once you have deleted the Vista one. The downside of this is that resizing partitions always carries the small risk of something going badly wrong and you losing the Ubuntu installation and your data.

As a first step, open a terminal and post the output of this command:

```
sudo fdisk -lu
```This will give us your partition layout and we can then see what is and what is not possible.

---

