---
title: "Slow shutdown after reinstalling Network Manager"
date: 2011-12-11
forum: General Help
---

### Post by zcacogp on 2011-12-11
Dear All, 

I have reinstalled Network Manager on my laptop, and while it works fine, it has caused the shutdown of the machine to become very slow. Shutdown time was quite brisk before and it now takes 5 minutes or more.

Interestingly, if the machine is *not* connected to the wireless network when asked to shut down, it shuts down almost instantly. (I took it to another location this evening, and it was beyond the reach of the network for the entire time it was on, and it shut down in less than 5 seconds - impressively fast - suggesting that the problem is related to the network connection.) 

I asked for help with making Network Manager work here: 

[http://ubuntuforums.org/showthread.php?t=1893089](http://ubuntuforums.org/showthread.php?t=1893089)

... many thanks to praseodym for his help. He suggested looking at three log files, as follows: 

/var/log/syslog
[http://www.sendspace.com/file/phsrgx](http://www.sendspace.com/file/phsrgx)

/var/log/dmesg
[http://www.sendspace.com/file/t78zct](http://www.sendspace.com/file/t78zct)

/var/log/Xorg.0.log
[http://www.sendspace.com/file/ug8zl4](http://www.sendspace.com/file/ug8zl4)

(all are a bit big to include as text in this post hence the download links.) 

The machine doesn't have any Samba shares on it, but it does connect to three Samba shares from another machine on the network. They autoconnect in fstab - which looks like this; 

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0b5b1d8e-eef1-4323-938c-3fe81aea73f2 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda8 during installation
UUID=d66f229b-2de1-4d82-b65c-62ba3c33ace1 none            swap    sw              0       0

/dev/sda5 /media/Horatio ntfs-3g defaults,locale-en_GB.utf8 0 0

/dev/sda6 /media/Ieuan ntfs-3g defaults,locale-en_GB.utf8 0 0

//desktop/Helena /media/Helena cifs credentials=/etc/samba/users,noexec 0 0

//desktop/Ianthe /media/Ianthe cifs credentials=/etc/samba/users,noexec 0 0

//desktop/cdrom /media/cdrom cifs credentials=/etc/samba/users,noexec 0 0

```

Machine details: IBM Thinkpad laptop running 11.04 32-bit, with built-in wireless card. 

If anyone can help I'd be most grateful - thank you. 


Oli.

---

### Post by zcacogp on 2011-12-15
Chaps, 

OK, it turns out that this is a known issue, and there are quite a number of threads about it. 

One of them is here: 

[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

... with a solution which worked for me. 


Oli.

---

