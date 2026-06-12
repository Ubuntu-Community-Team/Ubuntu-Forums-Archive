---
title: "how to access mac partitions"
date: 2012-07-02
forum: General Help
---

### Post by yilin on 2012-07-02
I've a triple booting xp-osx-ubuntu system. Currently
XP can access mac partitions but not ubuntu partitions
OSX can access XP(NTfs) partitions (read only), but not see Ubuntu partitions
Ubuntu can access windows partitions but not osx partitions

How can I get the access from ubuntu to osx ?  Thanks a lot

---

### Post by cwsnyder on 2012-07-02
According to [http://forum.xbmc.org/showthread.php?tid=51626](http://forum.xbmc.org/showthread.php?tid=51626) , you can force mount a HFS+ partition for R/W access, or there is a commercial utility from Paragon.  I have no experience with either of these solutions, however.

---

### Post by hal8000 on 2012-07-02
I'm very surprised that XP can see your OSX partition as mmy XP cant read nothing but NTFS and FAT32.

First post output of

sudo fdisk -l


Your OSX must be a primary partition and quite likely hfsplus filesystem,
type af. For reference looks like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    39070079    19535008+  83  Linux
/dev/sdb2        39070080    87891614    24410767+  83  Linux
/dev/sdb3   *    87891615   126961694    19535040   af  HFS / HFS+
--snip--

To mount the hfsplus partition create a mountpoint then mount the filesystem like this

 sudo mount /dev/sdb3 -t hfsplus /media/osx

The mountpoint has to be created first which in my case is /media/osx

A check on what is mount can be done with df:

 df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext4     19G  5.1G   13G  29% /
/dev/sdb2     ext4     23G   11G   13G  47% /home
/dev/sdb3  hfsplus     19G  5.0G   14G  27% /media/osx

Note that linux can only read from hfsplus partitions and not write to
them. Hope that helps.

---

### Post by yilin on 2012-07-02
> **hal8000 said:**
> I'm very surprised that XP can see your OSX partition as mmy XP cant read nothing but NTFS and FAT32.

I used macdrive utility in XP to get access to mac partition...

Thanks a lot cwsnyder and hal8000!    I'll try and see what I can have.

---

