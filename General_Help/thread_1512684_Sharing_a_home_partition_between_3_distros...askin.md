---
title: "Sharing a /home partition between 3 distros...asking for trouble?"
date: 2010-06-18
forum: General Help
---

### Post by Vunutus on 2010-06-18
On my netbook I want to have three linux distros: full desktop ubuntu, a quick loading web oriented netbook OS (maybe UNR or a couple others), and backtrack 4.

To save HD space, I was thinking about having like a 10GB partition for each OS, a 2GB swap partition to be shared, and a /home partition taking up the rest of the drive to be shared between all the OSes. Are there any potential complications here? Should I use a separate user and home folder for each distro or would it be ok to share the same home folder between all of them?

---

### Post by srs5694 on 2010-06-18
It should work fine, although it's a good idea to give each user a different home directory (/home/vunutus1 for distribution 1, /home/vunutus2 for distribution 2, etc.). Sometimes distributions have different versions of user programs and these programs write different configuration file formats, which can cause confusion when switching distributions. There can also be problems because icons may not exist in the same locations, so icon references in desktop GUIs may break across distributions. Different distributions may assign different user ID (UID) numbers, too. All these problems are easily corrected by using different home directories, even if they're on the same /home partition.

Note that forcing synchronization of UID numbers may be desirable, since it will enable easier access to your own files across distributions. This is true whether you share the /home partition or not.

---

### Post by philinux on 2010-06-18
> **Vunutus said:**
> On my netbook I want to have three linux distros: full desktop ubuntu, a quick loading web oriented netbook OS (maybe UNR or a couple others), and backtrack 4.

To save HD space, I was thinking about having like a 10GB partition for each OS, a 2GB swap partition to be shared, and a /home partition taking up the rest of the drive to be shared between all the OSes. Are there any potential complications here? Should I use a separate user and home folder for each distro or would it be ok to share the same home folder between all of them?

I would do it slightly different.

8 gig for each OS with there own home, not a separate partition. 2gig swap and the rest a /data partition. You can use the same username etc for all three or different if you choose.
You can always sync bookmarks by various means or just copy the config folders.

---

### Post by oldfred on 2010-06-18
I do it like philinux, but I try to move some of the data that gets saved into /home by default into /data. Firefox and thunderbird let you edit profile.ini to look in different places. Other programs may let you set a default path so /home ends up only with configuration files.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

