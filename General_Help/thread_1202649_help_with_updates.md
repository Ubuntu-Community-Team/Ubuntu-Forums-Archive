---
title: "help with updates"
date: 2009-07-02
forum: General Help
---

### Post by findit on 2009-07-02
I have installed the latest desktop version side by side with xp. Everything appears to be running fine so far, and and when i boot up ubuntu it automatically searched for the latest updates and listed them. The problem is when i go to install the updates it tells me there is not enough space. I have 2G of ram and assume this is not the problem, and plenty of hard drive space, although i did not move the slider bar any when i chose to install side by side. Everything else seems to be working fine with ubuntu for what i use it for.Can someone please help me. Thanks

---

### Post by raymondh on 2009-07-02
> **findit said:**
> I have installed the latest desktop version side by side with xp. Everything appears to be running fine so far, and and when i boot up ubuntu it automatically searched for the latest updates and listed them. The problem is when i go to install the updates it tells me there is not enough space. I have 2G of ram and assume this is not the problem, and plenty of hard drive space, although i did not move the slider bar any when i chose to install side by side. Everything else seems to be working fine with ubuntu for what i use it for.Can someone please help me. Thanks

Kindly post terminal (applications > accessories) outputs of

```
df -h
sudo fdsik -l
```

small L and not number 1

Thanks.

---

### Post by findit on 2009-07-02
Please forgive me I am new at this how do you get to enter the "sudo" command?

this is what i get when I try to update

Not enough free disk space

The upgrade needs a total of 356M free space on disk '/'. Please free at least an additional 322M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by raymondh on 2009-07-02
> **findit said:**
> Please forgive me I am new at this how do you get to enter the "sudo" command?

this is what i get when I try to update

Not enough free disk space

The upgrade needs a total of 356M free space on disk '/'. Please free at least an additional 322M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Hello Findit,

No worries :)

Access a terminal (applications > accessories) and type

```
sudo apt-get clean
```

You will be prompted for your password.  This is the same password you have to access ubuntu (configured when you installed Ubuntu).  When you type, the password will not be displayed in the terminal so do not worry.

Here are links for your reference...

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Now, since you are at terminal, how about also typing (one at a time)

```
df -h
sudo fdisk -l
```

Each command you type will give out certain outputs.  The first command will show you, more specifically, how much % of space has been used in your ubuntu install and it's specific 'folders' (in windows-speak).  The second command will tell us how your internal hard drive is configured.

If you may, just highlight, copy and paste the results directly as you post back.  

The reason I request those command outputs is because if you have allocated only so little space when you installed Ubuntu, then sooner or later, you will run into the same problem again ... no disc space. 

Better to learn of it now and try to correct rather than continously have this error in the future and experience frustration ;)

Your choice, as always.

---

### Post by drs305 on 2009-07-02
findit,

Welcome to Ubuntu and the Ubuntu forums.

I wrote a guide on finding out where a user's free space has disappeared to. I tried to make it self-explanatory so a new user could use it but there *are* quite a few terminal commands. 

It explains possible reasons a partition reports full, how to find it and most importantly, how to fix it. Click on the link in my signature line titled "DiskSpace".

---

### Post by findit on 2009-07-02
this is what came up. is there an easy fix or should i just start over, and if so how do I make it the correct size



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.3G  2.2G   43M  99% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  188K 1007M   1% /dev
tmpfs                1007M   76K 1007M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile



  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         850     6827593+   c  W95 FAT32 (LBA)
/dev/sda2   *         851       23669   183293617+   7  HPFS/NTFS
/dev/sda3           23670       24321     5237190    5  Extended
/dev/sda5           23996       24299     2441848+  83  Linux
/dev/sda6           24300       24321      176683+  82  Linux swap / Solaris
/dev/sda7           23670       23973     2441817   83  Linux
/dev/sda8           23974       23995      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by raymondh on 2009-07-02
> **findit said:**
> this is what came up. is there an easy fix or should i just start over, and if so how do I make it the correct size



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.3G  2.2G   43M  99% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  188K 1007M   1% /dev
tmpfs                1007M   76K 1007M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile



  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         850     6827593+   c  W95 FAT32 (LBA)
/dev/sda2   *         851       23669   183293617+   7  HPFS/NTFS
/dev/sda3           23670       24321     5237190    5  Extended
/dev/sda5           23996       24299     2441848+  83  Linux
/dev/sda6           24300       24321      176683+  82  Linux swap / Solaris
/dev/sda7           23670       23973     2441817   83  Linux
/dev/sda8           23974       23995      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order



Hello Findit,

Kindly back up your personal files ... there are no gurantees.

Did you install ubuntu twice? (  sda5 & sda6 as well as sda7 & sda8  )

Some notes ... root (/) needs about 4 GB.  Most recommend about 8-15.  

You may try resizing, taking the space from sda5 & 6.  Or, you may start fresh ... giving you the opportunity to create a separate /home partition as well.

If able, I always prefer to start fresh.

Reference links for reading

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

For installation

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

For a separate /home partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.linuxformat.co.uk/wiki/index.php/Creating_a_separate_home_partition](http://www.linuxformat.co.uk/wiki/index.php/Creating_a_separate_home_partition)

If you decide to start anew and create a separate /home partition, it can be done before the installation.  We will just have to point the installer to the appropriate partitions.  See this thread starting at post 6.

[http://ubuntuforums.org/showthread.php?t=1175277](http://ubuntuforums.org/showthread.php?t=1175277)

Let us know what you decide and we can assist you from there.  Good luck.

---

### Post by raymondh on 2009-07-02
Should you decide to resize (as well as deleting partitions to make space)...

Use a liveCD and in live session mode (TRY UBUNTU WITHOUT ANY CHANGES) as gparted will not work on any partition that is mounted.

In liveCD, and to access gparted, go to system > administration > partition editor.

In gparted and if the resize option is disabled (greyed-out), right click on the SWAP partition and choose SWAPOFF.

Good luck.  Back up first.

---

### Post by findit on 2009-07-02
Yes i have installed it twice thinking the first one did not work. I wouldn't mind starting fresh, but how do I do that. And more importantly how do I make sure there is at least 4G or 8G as suggested. Thanks.

---

### Post by findit on 2009-07-02
I would like to have a seperate home partition not to share with windows and have 2G ram

---

### Post by raymondh on 2009-07-03
Very well ... a couple of questions:

1.  Have you backed up your files elsewhere?
2.  How much space do you want to allocate for windows and how much for ubuntu?  You stated giving Ubuntu root (/) 8GB.  I would give SWAP about 1.5GB.  /home can take up the remainder.  As it stands, that's about 10GB already without counting /home.  Can you afford to give /home another 15GB (knowing that it will retain your settings, personal files, tweaks, etc)?  If not, and can only give Ubuntu less than 20GB, better to just have a straight-up-no-separate-/home-installation.
3.  Do you have the original XP install disc and not the recovery disc?

For a visual guide, can you post a screenshot of what gparted outputs?

[B]
Kindly read the links provided earlier re: partitioning and gparted.  It will give you an idea of what you are about to do.[/B]

Remember, in gparted, you will be asked ot review everything before it actually proceeds.

The process will be as follows :

1.  Back-up
2.  Defrag windows
3.  Boot into the liveCD and in live session (TRY UBUNTU WITHOUT CHANGES)
4.  To be sure, right click on the windows partition (hint : NTFS) and UNMOUNT
5.  Click on the linux partitions (swap, root) and delete, leaving them unallocated.  They are the ones formatted as 'ext'
6.  Click on the EXTENDED partition and delete as well.

Review and click Apply.

From here, you will end up with windows + unallocated space.  This is where you resize appropriately.

7.  Once resizing is done, you will now create an EXTENDED partition and **inside it** .... 3 partitions (_SWAP_, UBUNTU _ROOT_ (known as '/') and _/HOME_.

7.a.  Left click on the unallocated space.  Select **PARTITION** and select **NEW**. Make an **EXTENDED** partition and let it use all the free space.  Click APPLY.

7.b.  Click inside the extended partitions to make those 3 partitions (if you still want /home separate).

- SWAP partition, formatted in linux swap file system, size per your needs.
- EXT3 partition, formatted in EXT3, 8GB size  (this is for root)
- EXT3 partition, formatted in EXT3, use remaining space (your /home)

Click apply to create those 3 partitions.  After, quit and close gparted as you will now proceed with the installation.

8.  Proceeding with the installation, when you get to the partitioning stage, choose MANUAL
9.  Select the SWAP partition and click **EDIT** (see bottom of screen).  Select **USE** and type **SWAP**
10. Next, select the 8GB partition > EDIT  and select **USE**, **EXT3** and type **/**
11. Do the same for the remaining partition .. only changing type to **/home**

Continue with the installation.

I will log-off now.  If unsure of what to do, post back for clarifications until you are ready.  Also, kindly read the links to familiarize yourself.  It may seem daunting but with preparation, it'll be painless :)  I will check this thread tomorrow .

Some more links:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by raymondh on 2009-07-03
Only delete Ubuntu when you are ready to do so.  

When you installed ubuntu, GRUB overwrote into the MBR which now controls your booting.  If you delete Ubuntu and then pause the installation because of uncertainty, etc,.... you will have trouble accessing windows unless you fixmbr (for which, we need the original XP installation disc).

---

### Post by findit on 2009-07-03
I have 180GHD in which very little is used. everything in windows I have a backup, but no windows cd (nothing saved on ubuntu yet). First is there any way to uninstall and start over, second I would like to install ubuntu onto another computer with about same specs. But this time what do I have to do different so this does not happen again. Thanks

---

### Post by raymondh on 2009-07-03
Hi Findit,

Were you able to read the links I provided?  They will give you clues and answers to your questions as well as familairize yourself with what you are about to do :)

1.  Have you decided how much you want to allocate to unbuntu?  Depending on what you say, we may just delete one ubuntu install and increase the remaining ubuntu install..... we may resize what you have now .... we may delete and shrink windows ... etc. (so many options depending on what you decide to give ubuntu.

2.  Can you post a screenshot of gparted's output?  In ubuntu (or even a liveCD) go to system > administration > partition editor (gparted).  Once it opens, it will show your HD.  Keep it open.  Now, go to applications > accessories > take a screenshot.  Position the windows so that we can see gparted.  Take the screenshot and have it save in desktop.  Now, come back to the forum and post.  On the top menu of your post page (beside the smily), is the ATTACH icon (paperclip).  If you click on it, it will bring up another window.  Browse for your saved screenshot (it'll be in desktop) and LOAD.  Once done, go back to your post window and SUBMIT REPLY.

As the links will tell you, there are many ways to go about this.  We can:

1.  Guided resize
2.  Manual install
3.  Delete partitions and resize and then manual install


Kindly read the links and prepare..... decide how much you want to give Ubuntu....then we'll proceed.  

I am attaching a post/thread which underwent a similar issue as you had.  In this thread, OP (beesblas) created a blank/unallocated space for Ubuntu after resizing XP. All the forum can do is provide a guide.  You may want to PM him for his experience.

[http://ubuntuforums.org/showthread.php?t=1202483](http://ubuntuforums.org/showthread.php?t=1202483)

Good luck.

---

