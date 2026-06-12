---
title: "Multiple Installs (about 5)"
date: 2012-02-25
forum: General Help
---

### Post by amnite on 2012-02-25
So I always here about dual boot machines, matter of fact I am using one. But I bought a new desktop with a Terabyte hard drive. What I would like to do is quad maybe even 5 boot it. Is this possible. I need my everyday use os, Windows for gaming, new release testing os, my distro creation os, and another one... I dunno i never heard about anybody doing it.

---

### Post by mike555 on 2012-02-25
Yes you can (I do) but best to format ahead of time and make one swap partition (equal or bigger than installed RAM ) then when installing ,install grub to some partition as you are installing to..... then use bootup manager installed to mbr to boot the one you want ........ I use "GAG" from;    [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by amnite on 2012-02-25
> **mike555 said:**
> Yes you can (I do) but best to format ahead of time and make one swap partition (equal or bigger than installed RAM ) then when installing ,install grub to some partition as you are installing to..... then use bootup manager installed to mbr to boot the one you want ........ I use "GAG" from;    [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
What is the swap partition for? So if i want 5 os, then i need 6 partions, and a swap partition(7 total)? Sorry could you elaborate just a lil more

---

### Post by mike555 on 2012-02-25
Ok, start by using live ubuntu cd, use gparted to partition the hard drive , into 1 main partition and a extended partition with 6 inside it one being a swap partition (about 4Gb ) for linux distros .... lets say on a big hard drive the main is 100 gb , the extended is the rest and inside it make one swap partition , and divide up the rest, formating the main as ntfs (for Windows ) the rest ext4 (except the swap which should be formatted as swap)... 
then after install Windows first to the ntfs ,then linux to one of the others -making sure to install grub to the same partition -or it wont start...
 then install Gag and setup to be able to boot different ones ....... plop is another free bootup manager ...[http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)    ..and is more automatic and boots usb drives.... good to have on hand anyway..

 the reason for all this is because you can't make more then 4 primary partitions ,so make one and then the rest extended -which lets you make many inside it.

---

### Post by oldfred on 2012-02-25
On my larger drive I have multiple installs of Ubuntu. I use a common data (ext3) and shared (NTFS) partitions for almost all data and keep / (root) partitions at 20 to 25GB including /home. My XP is on another drive but reads the shared NTFS partition for Firefox & Tunderbird profiles. I now use XP very little.

You do have to keep track of partitions and which partition is the one you are booting from or has the working/main grub2 install. I use boot info script before & after each install so I both document system and understand it. I have installed to the wrong partition (only by luck was it also empty) so I revert to pencil & paper to document where to install. I still have some unallocated where I may add more / partitions or test something.

Attached is my partitioning.

I have used Herman's site for lots of detail on multiple drive installs.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

