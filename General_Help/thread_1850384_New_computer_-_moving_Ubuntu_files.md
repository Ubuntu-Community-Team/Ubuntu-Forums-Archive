---
title: "New computer - moving Ubuntu files"
date: 2011-09-26
forum: General Help
---

### Post by homer4421 on 2011-09-26
Hello,

I recently just got an i7 laptop which will replace my old old old (1  gig DDR1 RAM) AMD Turion64.  Since I'll have faster computing power, I'm  planning on making the i7 my primary laptop, however all of my Ubuntu  files are on my old laptop, and I'm not looking forward to figuring out  what packages I'll need to install (the ones aside from the normal updates) on my new laptop once I have Ubuntu  installed.

My question: Assuming I install the same version of Ubuntu on my new  laptop (11.04 x32), is there a way I can just move all the folders  on my old laptop onto my new laptop (including the root folders so I don't have to install the packages)?   Also, please note I am running/will be running Ubuntu on Windows machines, where Ubuntu is installed  alongside Windows (not on a partitioned drive).

Thanks for your help!

---

### Post by btindie on 2011-09-26
See [this]("http://ubuntuforums.org/showpost.php?p=1792628&postcount=3") post for how to install the same packages on your new system.

As simple as
```
old-system# dpkg --get-selections > /var/backups/dpkg-selections.txt
```
```
new-system# dpkg --set-selections < dpkg-selections.txt
```

You can even copy across your settings with debconf, will require debconf-utils to be installed
```
old-system# debconf-get-selections > /var/backups/debconf-selections.txt
```
```
new-system# debconf-set-selections debconf-selections.txt
```

---

### Post by collisionystm on 2011-09-26
> **homer4421 said:**
> Hello,

I recently just got an i7 laptop which will replace my old old old (1  gig DDR1 RAM) AMD Turion64.  Since I'll have faster computing power, I'm  planning on making the i7 my primary laptop, however all of my Ubuntu  files are on my old laptop, and I'm not looking forward to figuring out  what packages I'll need to install (the ones aside from the normal updates) on my new laptop once I have Ubuntu  installed.

My question: Assuming I install the same version of Ubuntu on my new  laptop (11.04 x32), is there a way I can just move all the folders  on my old laptop onto my new laptop (including the root folders so I don't have to install the packages)?   Also, please note I am running/will be running Ubuntu on Windows machines, where Ubuntu is installed  alongside Windows (not on a partitioned drive).

Thanks for your help!

Try to do a clonezilla move. 

Theoretically if you clonezilla your old computer and restore it on your new one, Ubuntu should automatically adapt to the new hardware. Unless you installed some sort of nvidia or ati driver. then you would just need to fix your xorg.

---

### Post by oldfred on 2011-09-26
Welcome to the forums.

You mention not partitioned but along side. Along side is partitioned but inside the NTFS partition is wubi. Are you running wubi. It is justa a file in the NTFS partition (root.disk).

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by bcbc on 2011-09-26
This discusses moving a wubi root.disk between machines:
[http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines](http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines)

---

### Post by homer4421 on 2011-09-26
Hello,

Thank you all for your help.  I'm sorry, I should have been more specific, I am using wubi.  I specifically want to move my Ubuntu files onto my new laptop and increase the Ubuntu storage size, as my new laptop has a larger hard disk.  Can someone please tell me how to do this?  The steps I'm thinking are

1. Backup Ubuntu files from old laptop
2. Install Ubuntu 11.04 on new laptop (with larger storage space)
3. Follow bcbc's steps on wubi (thanks again!)

Will this allow me to have my Ubuntu files with more space on my new laptop, and Is this procedure recommended?

Thanks again!

---

### Post by bcbc on 2011-09-26
No - the moving of the root.disk will keep the same space available. There are ways to increase this, but... if you are moving to a new PC, then why don't you partition and migrate the install to it. This is more stable than using Wubi's virtual disk, and you can then make it as big as you like.

---

### Post by oldfred on 2011-09-26
If you like Ubuntu enough that you want it on your new computer it is time to partition as bcbc says.

Even the developer of wubi expects you to partition:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

