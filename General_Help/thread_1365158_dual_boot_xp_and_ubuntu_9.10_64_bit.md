---
title: "dual boot xp and ubuntu 9.10 64 bit"
date: 2009-12-26
forum: General Help
---

### Post by mkapadia13 on 2009-12-26
Hello,

I know there are many topics on this, but I am having some trouble as I am new to Ubuntu.

I am trying to install Ubuntu on a hard drive with Win XP already installed.  In the partition step, I selected 'Manual Partition,' and have two rows in the table that both say 'Free Space.'  

How do I make them one?  It won't let me delete the smaller one.

Thanks.

//Moiz

---

### Post by audiomick on 2009-12-26
Hi
You can't delete free space. It is, in effect, already deleted, i.e. has no partition in it.

Are your two free spaces separated by a partition? If they are, you will have to move the sides of the partition one at a time to occupy the free space to one side, thus leaving the free space in one block.

Before doing this, you should have backed up anything valuable in the partition that is being manipulated.

---

### Post by mkapadia13 on 2009-12-26
Hi Michael,

Thanks, I didn't know that it worked in space order like that.  

Now I have all my free space, and I've set it to be 'ext4.'  I also have a portion allotted to 'swap.'  When I click Continue, I get a message saying:  "No root file system is defined.  Please correct this from the partitioning menu."

Any clue?

Thanks!

---

### Post by audiomick on 2009-12-26
Yes.
You need to have set a mount point for the space. The minimum is to set the mount point for one partition at /

The symbol / stands for the root of your file system.
In addition to that, there should be a swap partition. The system will theoretically run without swap space, but it is very strongly recommended to have one. If you want hibernate to function, swap must be as big as your RAM (or a fraction bigger)

It is also a good idea to set up a separate partition for /home. The home directory is where all your data and user configs get stored. If it is a separate partition, you can simply re-mount it at the stage of the instal you are at, should you have to do a fresh install at some point. Your data is then all still there where you put it, and your personal setup should still be intact as well.

A good set up is

Between 10 and 15GB, depending on how big your HD is, mounted at /
Swap at least 1GB, or as big as RAM, whichever is bigger
The rest of the available space mounted at /home

---

### Post by mkapadia13 on 2009-12-26
Michael,

Thanks so much for the advice.  I am up and running as per your recommendation.

Can you elaborate on the concept of having a partition mounted as /home though?

---

### Post by audiomick on 2009-12-27
It is fairly straightforward, but requires a few words. If you already know most of this, sorry...


If you do not specify otherwise, the file system is all on one partition. The file system starts at / and branches out from there. Home is inside / at /home. A directory inside home would be /home/directory, one inside that /home/directory/inside_that

In / , as well as /home, are a number of other directories. Amongst others /boot , /var , /etc , /lib , /media . These contain various system files and directories.

The mount point is the point within the filesystem where a directory appears. An example is USB drives and so on that are automatically mounted to /media/some_removable_drive_name . 

In this case, the USB drive is physically pugged in and removed. It is, however also possible to unmount any directory in your file system, or to add a directory practically anywhere.

It is possible to have any directory in it's own partition. It is also possible to have every partition on it's own HDD.

Some power users do in fact put system directories each on their own partition, on the one hand to use some of them for multiple installs, and on the other hand to re-use them for a new install.

For "normal" users, there is no call to do more than have a separate /home.

You have used the manual partitioning option in the installer, so you have seen how to set a mount point during the installation. If you were to have to do a fresh install (e.g. because you tried something out and broke you system completely :) ) and have a separate /home partition, you can simply mount it without formatting in the new install.

The system puts all you data in /home by default, and all your user options and configs and stuff. This means, if you spend hours messing around getting your desktop just the way you want it, your evolution e-mail happening, your firefox bookmarks set up, and so on, and then have to re-install for whatever reason, having /home in it's own partition means you can get back to where you were with no more effort than making sure all the programs are there that you had installed.

I think that is enough for now, but here is a link to info about partitioning. I think that could help you too.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

