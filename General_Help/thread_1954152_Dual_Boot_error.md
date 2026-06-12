---
title: "Dual Boot error"
date: 2012-04-07
forum: General Help
---

### Post by TomyK on 2012-04-07
Hello everewhun.
Although silent on the forums i keep an eye on the forums due to the extreme support they provide.
After a while i decided to remove 10.04 and install 11.10 fresh.
I have an issue though.
My job dictates that i use winblows 7 fo4r some apps made by our programmer so i need to have both OSes on my computer.
I have my win installed on C:\ and HAD my 10.04 on another hard drive though the dual boot system was working like a baus.
This time though things are different.
I formated the hard drive wich i had my ubuntu installed L:\ and tried to setup 11.10 on L:\ from scratch.
When i try to install it along winblows though it wont let choose the hard drive i want to install it to.
And when i try to choose what hard drive linux will be using and what drive winblows will be using (3rd choice on instalation method) i get an error msg sayin ''The basic file system is not defined'' or something liek that.
What do ubuntu-ers???

Thanks in advance.

---

### Post by PhantomTurtle on 2012-04-07
[http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/]("http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/"). Follow this tutorial. Also do NOT make a new partition on the Ubuntu hard drive using Windows. Do that using the Ubuntu installer.

---

### Post by oldfred on 2012-04-07
PhantomTurtle's link looks pretty good, I just would not create a separate /boot anymore. And it highlights the install of grub2's boot loader to sdb which is vital.

If you set BIOS to boot from sdb with grub2, you do not need EasyBCD in Windows. Grub2's menu will also offer Windows.  If for any reason you want to directly boot Windows you still have the Windows boot loader in sda and can boot that with BIOS or one time boot key.

A couple more links to instructions:

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
[http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/](http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/)

---

