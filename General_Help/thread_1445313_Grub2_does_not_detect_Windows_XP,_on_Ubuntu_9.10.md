---
title: "Grub2 does not detect Windows XP, on Ubuntu 9.10"
date: 2010-04-02
forum: General Help
---

### Post by Bruno De Barros on 2010-04-02
Hi, and thanks for taking the time to read my message.

I installed Ubuntu 9.10 yesterday on my computer. I had Windows XP and Windows 7 (I deleted the Windows 7 partition and installed Ubuntu 9.10). However, after installing Ubuntu, I couldn't access the grub boot menu. So I googled, and I found out how to make the menu show up again. That was okay. But Windows XP didn't show up. So I googled a bit more, searched the forums, and I added the following entry to my 40_custom file:

> 
menuentry "Microsoft Windows XP Professional (on /dev/sda5)" {
        set root=(hd0,5)
    insmod ntfs
    search --no-floppy --fs-uuid --set 9AB85D71B85D4CBF
    drivemap -s (hd0) ${root}
        chainloader +1
}
As far as I know, that should work. The uuid I entered there is the one that gparted told me was the uuid of the partition. However, this isn't working. I get a disk read error when I try to boot my Windows XP.

[IMG]http://img85.imageshack.us/img85/263/gparted.png[/IMG]

According to my gparted, my Windows XP drive is inside an extended partition? I wonder if that has any influence on why I'm getting the disk read error, or anything. It's either that, or my 40_custom entry is wrong. I've been trying to sort this out for a while now, and I'm afraid I'm not getting anywhere with it. :\

Thanks in advance.

---

### Post by oldfred on 2010-04-02
You must have installed XP after 7. Windows does not normally boot from an extended partition and the second install of windows boots from the first install and the first install has to be in a primary partition. You also do not have a swap partition, was that intentional.

There are a few here who have made it boot and I will give you a couple of links. I do not know enough to directly help. It is better/easier if it is in a primary partition. Since you still have primary partitions you may be able to move/copy it. I also saw once where someone used sfdisk to redefine partitions and moved a logical to a primary (required certain parameters on location and available primary partitions.

If you are installing another windows again:
[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

HOWTO: Moving/Copying Windows XP to another Partition 
[http://ubuntuforums.org/showthread.php?t=916146](http://ubuntuforums.org/showthread.php?t=916146)

These instructions were with the win7 but show how to recover a boot of XP or Vista/7 but usually its Vista or 7 that are installed second.
Repair 2 windows installs to get each to be able to have grub entries XP & Win7 or Vista
[http://ubuntuforums.org/showthread.php?t=1362297](http://ubuntuforums.org/showthread.php?t=1362297)
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)
Edit the Vista or Win7 boot loader
Fix the XP bootsector.
Add Vista to "menu.lst"
Move the boot files from XP to Vista

---

### Post by Bruno De Barros on 2010-04-02
Yes, I did install XP after installing Windows 7. It was intentional not to have any swap space, I wanted Linux to use all my physical memory without ever using swap memory, since it's more than enough to keep it running properly.

I think I am just going to back up all of my XP and delete its partition, then install it again in a primary partition and reinstall grub using the Live CD. 

Thanks for all your help, I'm definitely gonna need those links to guide me through all of this, especially the one about moving/copying the windows xp partition, I might end up going with that. :)

---

### Post by oldfred on 2010-04-02
I also think copying should work but it still will require some repairs as part of the boot files were in the win7 partition you deleted.

XP repair disk
[http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)
How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

