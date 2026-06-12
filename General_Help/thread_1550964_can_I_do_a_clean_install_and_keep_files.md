---
title: "can I do a clean install and keep files?"
date: 2010-08-11
forum: General Help
---

### Post by andthewicked on 2010-08-11
Hi, I am trying to figure out if I can just do a clean install and still be able to keep any files, ex. music, scripts, pics ect. without having to burn the contents to disk or upload them to an external device? I have like 150gs of info I need to save I have an external but it will take a long time to copy everything so if you know any way to do this wile doing a new install your the man

---

### Post by switch10 on 2010-08-11
The best way would be to have a separate /home partition.  Since you don't have a separate /home partition, there is no way (unless you do an upgrade), without backing up the files you need, and reinstalling.  
 
I strongly suggest separating the /home partition from the / partition, that way whenever you want to do a fresh install, it will be a breeze.

---

### Post by fragos on 2010-08-11
create a separate data partition on disk and move those files there. Then clean install into the old partition.

---

### Post by andthewicked on 2010-08-11
so lets say I had the partition on one hard drive and all the files I want on another and did a clean install on the drive with the partition then all the other files would transver over?

---

### Post by BurningSludge on 2010-08-11
[FONT=Comic Sans MS][SIZE=3]Backup your home folder to a separate form of media or partition.[/SIZE][/FONT]

---

### Post by SoFl W on 2010-08-11
It is highly advisable that you back up everything anyway before you attempt any changes to the hard drive.
On your next new install, make a separate home partition and that will save some aggravation in the future.  This time however you will need to do a back up.... which is always a good idea.

---

### Post by rwgale on 2010-08-11
You can create a new partition and then move your /home folder to it.
I have done it manually, but the following documentation sounds much more promising.

As everyone has said, backing-up data first.

The following Ubuntu community documentation link 
    * Aims to keep the system usable and the data all safe.
    * Prepares Partitions and fstab first then only tweaks fstab at the end
    * Uses rsync to move the files
          
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Good Luck!

---

### Post by andthewicked on 2010-08-11
just to make sure I understand this correctly, I can copy my home folder to an external device and do a new install and just move them back sorry this is kind of confusing

---

