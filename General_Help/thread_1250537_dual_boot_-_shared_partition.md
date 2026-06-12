---
title: "dual boot - shared partition"
date: 2009-08-26
forum: General Help
---

### Post by RaptorBot on 2009-08-26
hey, so here's my dilemma. 
been using ubuntu for a while, after switching from win7. love it, but i miss some of my software, ect... ( and yes. i've looked into wine, and am using it for some stuff already)

so , anyway... what i want is a shared partition that both operating systems can read, so i can store my files on a data partition, and reserve smaller partitions for the systems. 

that way, i should be able to always access my files, and using either system doesn't limit me in any way.

what's the correct way to do this? i want both operating systems to treat it like their own documents, for example ubuntu with it's home directory, and windows' /Users directory. 

i tried following a tutorial, but as of not understanding it properly, managed to prevent the desktop from starting and had to revert to the livecd to put the home directory back together.

could someone explain?

ps. (apologies for any wrongdoing on my part, forum-wise. first time and all, you know?)

---

### Post by tgeer43 on 2009-08-26
I don't think you actually want to (or can) physically merge the two home directories but it can be done in a smoke and mirrors kinda way.
See this post for the details:

[http://ubuntuforums.org/showthread.php?t=660116](http://ubuntuforums.org/showthread.php?t=660116)

Hope this helps,

tgeer

---

### Post by RaptorBot on 2009-08-26
> **tgeer43 said:**
> I don't think you actually want to (or can) physically merge the two home directories...
tgeer

well, you can change the location of a users documents in windows through the registry, so i assumed you might be able to just point at my ubuntu partition..

would it be better to partition a seperate area, or attempt to mount the ubuntu partition in windows in order to  access my stuff? probably using Ext2 IFS

---

### Post by bob-linux-user on 2009-08-26
Suggest back up your data then run the live cd and go to gparted the partition editor. You may need to turn off the swap file while doing this. Repartition as follows:

1st partition NTFS Windows
2nd partition EXT4 Ubuntu
3rd partition NTFS for your documents photos etc
4th partition Linux Swap

When done you can point "My Documents" in Windows at the 3rd partition. I use the Linux and Windows Versions of both Thunderbird and Firefox and store my profiles on the 3rd partition so that all my bookmarks and emails are automatically up to date whether I boot in Windows or Ubuntu.

---

### Post by tgeer43 on 2009-08-26
> **RaptorBot said:**
> well, you can change the location of a users documents in windows through the registry, so i assumed you might be able to just point at my ubuntu partition..
Yes, you can but in the link that I provided PeterJS explains why this is not a good idea.
 > **RaptorBot said:**
> would it be better to partition a seperate area, or attempt to mount the ubuntu partition in windows in order to  access my stuff? probably using Ext2 IFS
The latter. Before dumping Windows I ran pretty well seamlessly just by making sure that each OS mounted the other's partition and could read and write to it.

tgeer

---

### Post by gordintoronto on 2009-08-26
> **RaptorBot said:**
> hey, so here's my dilemma. 
been using ubuntu for a while, after switching from win7. love it, but i miss some of my software, ect... ( and yes. i've looked into wine, and am using it for some stuff already)

so , anyway... what i want is a shared partition... 

You have a dual boot with Windows 7?  Probably your Ubuntu has full access to your Windows partition.  If I open "computer" in Nautilus, one of the items which appears is "62.6 GB Media".  That's my Windows partition; if I double-click on it, it opens right up.  I have copied files over to it so I have something to play with in Windows 7.  (Ubuntu is my primary system.)

Windows 7 doesn't support EXT3, so it can't see my Ubuntu partition.

Um, I do have ntfsprogs and ntfs-3g installed, I'm not sure if they are part of a standard installation.

---

### Post by bodhi.zazen on 2009-08-26
> **gordintoronto said:**
> Windows 7 doesn't support EXT3, so it can't see my Ubuntu partition.

It can if you install the drivers.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

