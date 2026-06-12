---
title: "Dual boot &amp; FileSystem"
date: 2012-05-06
forum: General Help
---

### Post by jraj90 on 2012-05-06
Hi all,

   I have a system with 3 HDD. Basically I want to use 2 of them for dual OS (ubuntu & windows on each HDD), and the other for storage. 

I want the storage HDD to be mounted and accessible (read & write) regardless of which OS I boot into. Therefore, I would like to know the most appropriate FileSystem to use on the storage HDD. 

After doing some research, I am thinking of using the ext4 for the storage, and get some 3rd party tools to mount and access the storage HDD whenever I am using Windows.

Is this a good solution? I would appreciate if you guys can give your point of view and tip.

At the moment, nothing has been done onto all 3 HDD. I am planning on installing Ubuntu on the 1st HDD, then proceed with Windows7 onto the second.

Thanks

---

### Post by Cheesemill on 2012-05-06
For the storage drive I'd go for NTFS as both Windows and Ubuntu can read/write NTFS out of the box with no extra 3rd party software needed.

I'd also recommend installing Windows first, then Ubuntu as Windows has a habit of wiping the MBR leaving you unable to boot into Ubuntu without first fixing grub.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Prescilla on 2012-05-06
I agree with Cheese.

Go with NTFS and you'll have no problem.

And yes Windows first, then other OS you want to install.

---

### Post by jraj90 on 2012-05-06
first and foremost, thanks for the tips.

so basically, installs windows first onto my first HDD, then install ubuntu onto the 2nd HDD.

and also, I need to ensure that the windows hdd is the first boot order?

---

### Post by Bucky Ball on 2012-05-06
Windows = install first onto first partition (primary), first drive;
Ubuntu = install next wherever you fancy (on primary, logical inside an extended partition, partition on another drive, wherever);
BIOS = set to boot from the first drive (the one your machine calls sda or hd0).

---

### Post by jraj90 on 2012-05-06
ok cool...


let me get the windows installed first onto my first HDD rather than the Ubuntu...

will let u guys know shortly how it went.

thanks again..

---

### Post by oldfred on 2012-05-06
You really want to keep Windows boot loader on the Windows drive and the grub2 boot loader on the Ubuntu drive. But installers like to install to either sda or the drive they see as boot from BIOS. So set BIOS to boot that drive for installing Windows or it may install its boot loader to the boot drive.

With Ubuntu you can choose if you use manual install. See last link and combo box to choose drive.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Then set BIOS to boot Ubuntu drive.

I also like to keep system partitions smaller, although Windows has to be a lot larger than Ubuntu and keep data in data partitions, shared partitions or for Ubuntu /home. If most data is in a shared NTFS you do not even need a separate /home, although most of us often suggest it.

---

### Post by jraj90 on 2012-05-06
the only reason i am wanting to install windows is gaming, and the use of office tools and visio..

anyways, i have simply plugged out my second HDD (which is meant for ubuntu)

currently in the process of installing the windows OS...

my last windows i used was XP :)

---

### Post by jraj90 on 2012-05-06
If I were to plug out my first HDD (Windows), then perform the UBuntu installation onto the second HDD. After that, plug in back the Windows drive, and set as 1st boot in BIOS, will this cause any problem. I would still be able to chose from windows / ubuntu OS rite ?

---

### Post by oldfred on 2012-05-06
Keep Windows as first drive, and set BIOS to boot Ubuntu drive.

Then to get grub2 to find Windows install, run this from Ubuntu and it should add Windows to the grub menu.
```

sudo update-grub
```

---

### Post by jraj90 on 2012-05-06
hi guys,

  wanna thank everyone here for your tips and also time. the system is working just the way I wanted.


thanks again everyone


regards

---

