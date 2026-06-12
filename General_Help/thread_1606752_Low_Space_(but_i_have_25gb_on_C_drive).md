---
title: "Low Space (but i have 25gb on C drive)"
date: 2010-10-26
forum: General Help
---

### Post by Rokett on 2010-10-26
i just started to use Ubuntu's last version like 5 hours ago (i believe its 10something).
-
Right now i have Windows Vista and Ubuntu on the same computer.
Im trying to install/move  some files on ubuntu but i get error message  that says, "Low dist space". But i have 20gb avaible on Vista.
So how can I have that 20gb on ubuntu also, like i wanna share that amount between Win and Ubuntu.
-
As i said before im using this OS for like [COLOR="Red"]5hours[/COLOR] so i dont know too much about it, i now where is terminal and how to get softwares, updates packets and stuffs like that but thats all. Consequently if you are going to give me Some Terminal codes or stuff, please try to as clear as you can....
Thank you so much.

---

### Post by papibe on 2010-10-26
There's an easy way, that requires several clicks each time, and a more user friendly solution (that unfortunately requires more advance work).

Easy: your windows files are available on Ubuntu. Go to Places -> Computer. There, look for a disk called something like "250GB Hard Drive: OS" (250GB is the size of my disk). Double click on it and you'll be on the root of your windows drive. Avoid modifying any file. Depending on your windows version click:

[INDENT]Users -> youruser -> Documents (Vista), or
Documents and Settings -> youruser -> My Documents (XP)[/INDENT]

The downside is that you'll need to be careful and just use your user files. Also, you always need to click, and click to get there.

Good Luck!

---

### Post by Rokett on 2010-10-27
> **papibe said:**
> There's an easy way, that requires several clicks each time, and a more user friendly solution (that unfortunately requires more advance work).

Easy: your windows files are available on Ubuntu. Go to Places -> Computer. There, look for a disk called something like "250GB Hard Drive: OS" (250GB is the size of my disk). Double click on it and you'll be on the root of your windows drive. Avoid modifying any file. Depending on your windows version click:

[INDENT]Users -> youruser -> Documents (Vista), or
Documents and Settings -> youruser -> My Documents (XP)[/INDENT]

The downside is that you'll need to be careful and just use your user files. Also, you always need to click, and click to get there.

Good Luck!
[http://yfrog.com/1fscreenshotvbp](http://yfrog.com/1fscreenshotvbp)
[http://yfrog.com/50screenshot1xkip](http://yfrog.com/50screenshot1xkip)
This is all i get :/ i dont see my windows root 
(also when i click on the "root" file it says, you do not have a permission )

---

### Post by Mark Phelps on 2010-10-27
I'm having this uneasy feeling that you are low on space because you installed Ubuntu inside Vista -- using the Wubi installer.  The default space allocation for those installations is very small, so small that you very quickly can run out of space.

When in Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  You will see a list of partitions.  If all of them say NTFS, then you have a Wubi install and you can NOT use standard partitioning tools to change the space allocation.

---

### Post by Rokett on 2010-10-27
> **Mark Phelps said:**
> I'm having this uneasy feeling that you are low on space because you installed Ubuntu inside Vista -- using the Wubi installer.  The default space allocation for those installations is very small, so small that you very quickly can run out of space.

When in Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  You will see a list of partitions.  If all of them say NTFS, then you have a Wubi install and you can NOT use standard partitioning tools to change the space allocation.


This is exactly what i got 
---

levent@ubuntu:~$  sudo fdisk -lu
[sudo] password for levent: 
Sorry, try again.
[sudo] password for levent: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112640    21084159    10485760    7  HPFS/NTFS
/dev/sda3   *    21084160   307333119   143124480    7  HPFS/NTFS
/dev/sda4       307333120   312578047     2622464    f  W95 Ext'd (LBA)
/dev/sda5       307335168   312578047     2621440   dd  Unknown

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89d780d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS
levent@ubuntu:~$ ^C
levent@ubuntu:~$ ^C
levent@ubuntu:~$

---

### Post by Rokett on 2010-10-27
Someone should help me or im going to delete ubuntu, because i cant put files i want it :/

---

### Post by oldfred on 2010-10-27
I am not familiar with wubi. But have saved some links. Wubi is for trying out Ubuntu without having to modify partitions as it creates its system as a file within the windows NTFS partition. How large did you make your original install? Usually it is 30GB which should be plenty for a significant test of Ubuntu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

### Post by CharlesA on 2010-10-27
Wubi creates an 8GB partition by default. There are ways to increase it without reinstalling, but they can be a bit complicated.

Also note: Wubi is generally used to "try out" Ubuntu, and isn't really suited for full-time use.

---

### Post by Rokett on 2010-10-28
> **CharlesA said:**
> Wubi creates an 8GB partition by default. There are ways to increase it without reinstalling, but they can be a bit complicated.

Also note: Wubi is generally used to "try out" Ubuntu, and isn't really suited for full-time use.

--
is there anyway to see my empty space on ubuntu, without uninstalling  Vista? i just delete some files from my vista and now i have 30gb space...
i just want to learn the way the share that 30gb

---

### Post by CharlesA on 2010-10-28
You could create a 30GB partition in Windows but I don't know if it'll be seen from Wubi.

---

### Post by Rokett on 2010-10-28
> **CharlesA said:**
> You could create a 30GB partition in Windows but I don't know if it'll be seen from Wubi.

--
there is should be a way, because i really like this system i dont wanna uninstall, but i need my stuffs in here not in vista

---

### Post by CharlesA on 2010-10-28
> **Rokett said:**
> --
there is should be a way, because i really like this system i dont wanna uninstall, but i need my stuffs in here not in vista

Could probably try running this from a terminal inside Wubi and seeing if it sees the 30GB partition:

```
sudo fdisk -l
```

---

### Post by Rokett on 2010-10-28
> **CharlesA said:**
> Could probably try running this from a terminal inside Wubi and seeing if it sees the 30GB partition:

```
sudo fdisk -l
```

I got this

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       19131   143124480    7  HPFS/NTFS
/dev/sda4           19131       19458     2622464    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2621440   dd  Unknown
levent@ubuntu:~$
```

---

### Post by CharlesA on 2010-10-28
I'm not sure what partition it is since it doesn't show the sizes. What did you format it is?

---

### Post by Rokett on 2010-10-28
> **CharlesA said:**
> I'm not sure what partition it is since it doesn't show the sizes. What did you format it is?

can you clear that sentence  because i didnt understand 
"What did you format it is"

---

### Post by CharlesA on 2010-10-28
When you created the partition in Windows, did you format it as FAT32 or NTFS?

---

### Post by Rokett on 2010-10-28
> **CharlesA said:**
> When you created the partition in Windows, did you format it as FAT32 or NTFS?

im not sure, but  i guess it was NTFS

---

### Post by CharlesA on 2010-10-28
Ok, verify how big that partition is and what file system it is and give it a label, that way you can see what partition it is.

---

### Post by Rokett on 2010-10-28
> **CharlesA said:**
> Ok, verify how big that partition is and what file system it is and give it a label, that way you can see what partition it is.

i really dont know that system, you should tell me where to get these info-s. im sorry :/ 
i can give you msn or facebook for make that process faster :/

---

### Post by CharlesA on 2010-10-28
Vista should have a disk management area:

Start > Right click computer > manage > disk management

---

### Post by Rokett on 2010-10-30
> **CharlesA said:**
> Vista should have a disk management area:

Start > Right click computer > manage > disk management


Sorry for late reply, yeah that space is available on disk management, i guess problem is with ubuntu

---

### Post by Verbeck on 2010-10-30
open up[B] places > compuer > file system
[/B] 
open up the folder named **host**. what do you see? normally the windows partition (c drive) should be there. all the other partitions ( d/e/f/g) should be available under the places menu.

on a side note, as already posted before, wubi is not for long term use. you might run into some trouble that doesn't occur in a normal install. try reading up dual booting : [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Verbeck on 2010-10-30
just did a wubi install from windows 7 in virtualbox  to see how things are. 
the **host folder in computer > file system** is your C: drive

---

### Post by Rokett on 2010-11-02
> **Verbeck said:**
> just did a wubi install from windows 7 in virtualbox  to see how things are. 
the **host folder in computer > file system** is your C: drive


i have a another question but this is the serious one...
If i format my driver ( i will do it anyways its just the time)
and if i dont instan Windows and just install UBUNTU,
AM I ABLE TO USE ADOBE CS5 series also their add-ons (photoshop Illustration, flash etc) With WINE but,   without writing to many stuffs into terminal ? i have a WIN setup, i was going to try that but i have no space on ubuntu as all of you know...
thats my question thank you..
Also am i able to install games with wine without using terminal ?
like Assassing Creed, fallout , batman , bioshock , silkroad online etc etc..

---

