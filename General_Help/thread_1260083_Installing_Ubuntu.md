---
title: "Installing Ubuntu"
date: 2009-09-07
forum: General Help
---

### Post by Fands on 2009-09-07
I have just installed Ubunto( Version 8.04 I think) as a duel boot with Windows XP home on a laptop.


  Even though i formatted a partition to install it on, but when at the question of where to install it during the installation process I requested “select partition manually” but it came back with a error, “partition wrong format type”, I’m aware the Ubunto works its own format type along with FAT32 so I assumed it would just re formatted to what it wanted.
   
      So I selected “Biggest space available”, thinking it would see the empty 26 Gig partition (50% of hard drive) but it ignored it and installed in on the same partition as windows.


 Subsequently when it find updates it can’t install them as it says insufficient disk space to install them even though there a 26gig partition to use.
  Ive looked around to see if I can uninstall it and start again, but can’t see how ?
 Can I move the installation to the unused partition with out uninstalling?
   
  Also, a side note,  I cant see the “filesystem” files when in windows, first though this was due to the format being NTFS, but the files are on there so it can’t be can it ?
   
  And again, Also I have to manually enter the Wifi 26 digit key every time I boot it, is there no way to store this information like you can on Windows ?
   
   
  Really appreciate any help guys
   
  Many thanks in Anticipation.

---

### Post by nothingspecial on 2009-09-07
Can you please post the output of 
```

sudo fdisk -l
```

and 
```

df -h
```

Open a terminal in your menus applications > accessories > terminal

---

### Post by ad_267 on 2009-09-07
You can move partitions around using the partition editor (Gparted) from the live CD (Go to System - Administration - Partition Editor), but this will make Ubuntu unable to boot unless you fix the boot loader. It would be easier to simply delete your Ubuntu partition, resize the Windows partition to take up the space that was taken by Ubuntu and then set up your own partitions manually.

When you use the manual partitioning method, you have to select what type of file system to use from the drop down menu (ext3 or ext4 is best) and tick the box to format the partition. You need to select the Ubuntu partition to be mounted at "/".

Windows cannot read the file systems used by Linux. There are drivers available but from what I've heard they aren't great. It would be a better idea to create an ntfs data partition to store data shared by Ubuntu and Windows.

---

### Post by nothingspecial on 2009-09-07
> **ad_267 said:**
> You can move partitions around using the partition editor (Gparted) from the live CD (Go to System - Administration - Partition Editor), but this will make Ubuntu unable to boot unless you fix the boot loader. 

We may be lucky in that if the partitions are in the right places the OP could simply delete the empty partition and grow the Ubutu one into it.

---

### Post by Fands on 2009-09-07
Thanks Guys !

Thant was quick, I'm at work now and the laptop with it on is at home so will post back tonight with the info requested, thanks for the help.

---

### Post by Fands on 2009-09-07
Having 
loaded the comand as follows

fDisk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d7f5ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3396    27270337+   f  W95 Ext'd (LBA)
/dev/sda2   *        3397        4863    11783677+   7  HPFS/NTFS
/dev/sda5               2        3070    24651711    7  HPFS/NTFS
/dev/sda6            3071        3374     2441848+  83  Linux
/dev/sda7            3375        3396      176683+  82  Linux swap / Solaris
fred@fred-laptop:~$

---

### Post by Fands on 2009-09-07
It has let use df -h as follows:


fred@fred-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G   58M  98% /
tmpfs                 233M     0  233M   0% /lib/init/rw
varrun                233M  104K  233M   1% /var/run
varlock               233M     0  233M   0% /var/lock
udev                  233M  148K  233M   1% /dev
tmpfs                 233M  112K  233M   1% /dev/shm
lrm                   233M  2.4M  231M   2% /lib/modules/2.6.28-11-generic/volatile

any use ?

---

### Post by nothingspecial on 2009-09-08
> **Fands said:**
> Having 
loaded the comand as follows

fDisk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d7f5ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3396    27270337+   f  W95 Ext'd (LBA)
/dev/sda2   *        3397        4863    11783677+   7  HPFS/NTFS
/dev/sda5               2        3070    24651711    7  HPFS/NTFS
/dev/sda6            3071        3374     2441848+  83  Linux
/dev/sda7            3375        3396      176683+  82  Linux swap / Solaris
fred@fred-laptop:~$

/dev/sda6 is your tiny Ubuntu partition.
/dev/sda2 is windows
/dev/sda5 is the empty on
I`m not sure what /dev/sda1 is, do you have a recovery partition.

Anyway, first things first. Back up anything you don`t want to loose then boot your live cd.

In the menu go system > administration > partition editor. This will fire up a nice partition editing gui. With this you`ll be able to check which partition is which.

You want to delete your empty 26 gig partition and resize the tiny Ubuntu one into it. Unfortunately this may not be possible without moving them and as ad_267 said this will mess up booting. If that is the case then delete both partitions (this will wipe Ubuntu) and make them one partition - format them to ext3. Install Ubuntu to that new partition.

During the install, instead of choosing largest available space, choose manual. Do not touch the windows partition. Choose to edit the empty partition. The one that is now ext3. Choose a mount point of /. Check the format box and choose ext3.

That should fix it. If your not sure about anything just ask before you do it. If you get it wrong you could loose everything.

---

### Post by kopiko on 2009-09-08
Do not touch the windows partition.
[[color=#FFFFFF]_ financement automobile | simulation credit | comparatif taux pret auto | calcul voiture _[/color]](http://simulationcreditauto.org)[color=#FFFFFF]une simulation crédit auto, le souscripteur doit remplir des renseignements[/color][[color=#FFFFFF]_ financement automobile | simulation credit | comparatif taux pret auto | calcul voiture _[/color]](http://simulationcreditauto.org)

---

### Post by Fands on 2009-09-08
Thanks guy will have a play with that.
this laptop is just a spare one hence why i'm using to to lean/play with linux.
There is no critical software on there so no big problem.

thanks again.

BTW any idea on the router password, can it be saved so i don't have to enter the 26 diigt each time i boot into Unbuntu ?

---

### Post by P4man on 2009-09-08
> **Fands said:**
> 

BTW any idea on the router password, can it be saved so i don't have to enter the 26 diigt each time i boot into Unbuntu ?

It saves it automatically afaik. I think you made a mistake though; the first time you connected, it probably asked you 2 things: the wep/wpa key for your wireless (26 digits), then it may have asked you wether or not to store the password in the "keyring". Im not sure what you answered there, if you said "yes", it could have asked you to set a password for the keyring -which is not the same as the wpa password, its a password that will unlock ALL passwords stored in the keyring, also for things like email or whatever apps making use of it.

Normally, you'd type in the same password for the keyring as you do for your account. in that case, the keyring will be unlocked automatically when you log in. If you set a different password, it will ask for the keyring password once per session; Is it possible you set your wpa password as keyring password?

---

