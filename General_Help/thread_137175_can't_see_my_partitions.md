---
title: "can't see my partitions"
date: 2006-02-27
forum: General Help
---

### Post by damu on 2006-02-27
.My first hard drive  looks like this :
C - primary - NTFS ...Win XP
* - primary - ext3 ...Studio to Go!
* - logical - ext3 ...Kubuntu (HDA3)
* - logical - swap
* - logical - fat32 ...data

.I also have another SATA hard drive with one ext3 partition. :???: 

Only one partition (hda3 where Kubuntu is installed) is seen in "media".
I could see them at the partitionning step during the installation though.
How to go round that? Do I need to change the fstab?

Once this is sorted I would like my home folder to be the logical fat32 partition by default. Is it to set that?

Thanks! ;)

---

### Post by aysiu on 2006-02-27
Making your /home folder FAT32 is a bad idea.
Mounting is a totally separate issue. If you want to *see* your partitions, follow [these instructions](http://www.psychocats.net/linux/mountwindows.php).

---

### Post by vbmaster on 2006-02-27
first you have to know the match of the partition you want in /dev/. To do that goto system menu -> administration -> disks and see, to your disk, the partitions tab, mainly the reference of the partition you want.

If you see that your fat32 is the /dev/hdb1 you just have to add this to fstab:

/dev/hdb1       /media/nameyouwant vfat    iocharset=utf8,umask=000   0       0

and then in a console

$ sudo mount /media/nameyouwant

To ntfs partitions do this:

/dev/hdb1       /media/nameyouwant  ntfs    nls=utf8,umask=0222 0       0

Stay co0l ;)

---

### Post by damu on 2006-02-27
Thanks both of you for your replies

I want my datas(including Kontact datas) to be on a separate partition.
I also need to access these datas form both Kubuntu and XP (at least till the latest Director and Flash works with Wine and that I have everything  working under Kubuntu... ;) )
So I didn't see any other way round that than using a fat32 partition.

aysiu, Why do you think it is a wrong idea?

Any comment welcome...

---

### Post by aysiu on 2006-02-27
*data partition* does not mean */home partition* necessarily.

FAT32 for /home is a bad idea because FAT32 is not designed for Linux and does not support Linux permissions. It's okay to put data files on FAT32 (pictures, music, documents, etc.), but configuration files and user folders should not be on FAT32.

You can make your /home partition very small or not even have a /home partition, just a /home folder. Then you can put a symlink from your FAT32 data partition to your /home folder (a symlink is like a Windows shortcut or a Mac alias).

---

### Post by damu on 2006-02-27
Thanks bunch for your explanations!

Home is actually a folder in the Kubuntu and I will definitely use your suggestion of a symlink.
Do you think it is safe to change the default data folder of Kontact (wherever it may be!) to this  fat 32 partition , or is this part of the thing you wouldn't recommend, in which case I would backup on a daily basis Kontact datas with Konserve?

I try to get the priniciple of what you said... I learn...sooo, I went to check on my partner's laptop  , which is already on Kubuntu (yep, I strongly recommended to her to do the switch before me!!!...and she is quite happy with it ...:) )

Soo, she has a home folder and not a home partition. Nevertheless, tI could only see her personnal files in it (pictures, music, documents, etc.), no configuration files. Would it be any different if it was a home partition?

---

### Post by vbmaster on 2006-02-27
I only have my personal documents, music, shit & stuff in a fat32 partition because that way I can play with the files in my both systems (ubuntu and xp), and I think that's the only advantage... ;)

---

### Post by damu on 2006-02-28
First, I would like to say to the other newbies like me reading this thread, that thanks to the answers given to me in that thread, I discovered that most of your personnal essential datas (like all the ones in Kontact and other softwares) are save by default somewhere in the home folder. You can't see it till you tick the option to see "hidden files" (view/show hidden files in Konqueror). ;) 
Ok, advanced users might say...duh!...obvious... :rolleyes:  well, it is a very important information for me , as I guess for any other person which intends to run its business with a linux distro...then backup becomes essential...and for an efficient  backup, you need first to know where are the datas you want to back up!  

My partition problem is not solved though.  :-k 
I followed your advice , vbmaster, and added 2 lines in the fstab file (one for hda5 the fat 32 partition, and one for sdb1 ext3 partition on another sata HD).
I can now see the icons of hda5 and sdb1 in /media/ , but when I try to sudo mount them, I get :
```

can't find hda5 in ect/fstab or ect/mtab
```

I then tried to plug an external hard drive and also a usb key, so that I could save fstab on a fat32 and post it here from XP.
In both cases, I get :
```
An error occured while loading media:/sdb:
The file or folder media:/sdb does not exist
```

On another laptop with Kubuntu Hoary, I can plug a usb key and transfer datas without any problem...

Some more infos about my system :
Asus A8V deluxe
AMD X2 3800+
2 Go of DDR
1ultra ATA HD (with hda3 for Kubuntu, hda5 for fat 32,...)
1 SATA HD
Kubuntu for AMD 64

Many thanks,

---

### Post by vbmaster on 2006-02-28
Why **ect/fstab** ?

It was supposed to be **/etc/fstab**... 

:|

---

### Post by damu on 2006-02-28
Sorry, it is probably /etc/fstab

The thing is, I have no way to share datas from Kubuntu to XP...soo, at the moment I try on Kubuntu, write on paper the result, boot on XP and send you the result...an easy way to miss a "/" .... :-?

---

### Post by tadashi on 2006-02-28
I do the same thing with my FAT32 for the same reasons.  I did try to make my home in the FAT32 but Kubuntu will not let you probably because of the permissions mentioned before.  I still have my XP partition, even though I rarely boot it. :p  But still want to access my data files, music, etc from both Linux and XP.

As for the USB drive, this is a common issue of recent.  You will need to either use the package manager and hit the upgrade button, then commit (should be about 125 packages to be upgraded) or
$ sudo apt-get update
$ sudo apt-get upgrades
Then reboot.  I think in the package manager I had to enable the univer and the multiuniverse repositories.  I also added the Kubuntu KDE repository to upgrade from KDE 3.4.3 to 3.5.1.

Good Luck.

---

