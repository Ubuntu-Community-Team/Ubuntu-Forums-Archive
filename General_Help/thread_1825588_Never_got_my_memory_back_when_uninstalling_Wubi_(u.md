---
title: "Never got my memory back when uninstalling Wubi (ubuntu)"
date: 2011-08-15
forum: General Help
---

### Post by rk111600 on 2011-08-15
Well, This is my first post on the forums...So, Hi.
But the reason why I'm posting is because I can't seem to get the memory back after uninstalling ubuntu 11.04 using the wubi uninstaller. The reason why I was uninstalling was because ubuntu didn't want to boot up, not even when I went into recovery mode (Correct me if that's not what it's called.) So, from there I just decided to uninstall it, Then I got an error from wubi. So I found an uninstall guide, it said if having problems trying to uninstall, try the uninstall_ubuntu.exe, It removed it, But I still haven't received my 20gbs that I set for wubi. In case if you guys need, I'm using a lenovo t400 thinkpad laptop with Windows 7 Ultimate. 3gbs of ram, 70gb hardrive, 32 bit os, Intel core 2 duo cpu @ 2.40 ghz for both cores, and ati mobility radeon hd 3400 series.

Thanks for your time.

---

### Post by Elfy on 2011-08-15
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

### Post by bcbc on 2011-08-15
This is a possible explanation ;)

In some cases (hard poweroffs, hardware incompatibility) it's possible that the virtual disk Wubi uses was corrupted. When this happens (and the corruption is on the ntfs filesystem), Windows can trigger a chkdsk that will try to repair the damage. Very often it will remove the virtual disk and place it in a recovery folder **\found.000**. 

One of the symptoms of this is... Ubuntu not booting. But if you uninstalled it wouldn't have looked in \found.000 so it's possible the virtual disk is sitting there taking up space.

So that's where I'd look. (PS found.000 is hidden, so you'll have to tweak things to find it or use the command line). The file will likely be renamed file0000.chk. If the whole disks directory is corrupted then you'll find a directory dir0000.chk and within that the root.disk etc. 

Just delete them to recover space, or if you had some data you want... there is a tool you can use from windows: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

---

### Post by rk111600 on 2011-08-16
Alright, I'll look for this file. Thanks.

---

