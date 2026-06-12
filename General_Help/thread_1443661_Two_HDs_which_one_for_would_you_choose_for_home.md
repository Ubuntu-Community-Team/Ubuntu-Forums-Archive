---
title: "Two HDs which one for would you choose for /home"
date: 2010-03-31
forum: General Help
---

### Post by clancymf on 2010-03-31
I have just added an additional 1 tb drive to my system.  Before I upgrade to 10.04 which should i choose to put my /home folder on and which should contain my sytem files and backup folder:

1. 1 TB 16 mb cache; or
2. 1 TB 64 mb cache

Also should I format the drive ext4 or ext3?

Thanks for your feedback!

---

### Post by johngreth on 2010-03-31
ext4 is the latest and greatest, but it has sever disadvantages. There are known bugs that can cause data loss and I've also heard about problems with destroying hard drives that may be related to the use of ext4. However, these cases are uncommon. So, if you want the very best and are willing to take the risks, go with ext4. If you want something that's well tested and well supported, ext3 is the way to go.

See also:
[http://en.wikipedia.org/wiki/Ext4#Disadvantages](http://en.wikipedia.org/wiki/Ext4#Disadvantages)
[http://ubuntuforums.org/showthread.php?t=1170802](http://ubuntuforums.org/showthread.php?t=1170802)

[http://ubuntuforums.org/showthread.php?t=1416482](http://ubuntuforums.org/showthread.php?t=1416482)
> **What makes 9.10 unique from the earlier versions is it's the first one to use Ext4 filesystem as the default (and yeah, it uses the new GRUB2, but that's very unlikely to be the problem).**

As for where to put what, I think it would be faster if the files/home directory were on the higher cache drive because those files get changed more often.

---

### Post by clancymf on 2010-04-01
Thanks so much for the reply and info!

---

