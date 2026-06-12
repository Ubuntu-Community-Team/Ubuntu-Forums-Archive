---
title: "clamdscan refuses to scan anything"
date: 2011-01-19
forum: General Help
---

### Post by flamadiddle on 2011-01-19
Not sure what's going on here.  I've installed clamav, clamav-freshclam and clamav-daemon to run automated scans on my machine running _Ubuntu Desktop 10.04 LTS x64_.

Unfortunately, clamdscan refuses to scan anything.

```
root@uhs:/raid/Share/Public/# clamdscan -v /raid/Share/Public/
/raid/Share/Public: lstat() failed: Permission denied. ERROR

----------- SCAN SUMMARY -----------
Infected files: 0
Total errors: 1
Time: 0.004 sec (0 m 0 s)
root@uhs:/raid/Share/Public/# 

```

/raid/Share/Public has 777 permissions, and the clamav-daemon user (clamav) has been added to both the admin and root groups.  I get the same error no matter what I try to scan.

I even ran `dpkg-reconfigure clamav-base` and made the daemon user `root` to see if that would help (which it didn't).  And I have of course run `service clamav-daemon restart` in between all of these changes.

I'm aware of the `cat file_name | clamdscan -` option, but I need to be able to scan whole directories, so obviously this won't work.

What's going on here?  Can I use clamdscan?

Thank you for any help.

---

### Post by flamadiddle on 2011-01-19
Further information regarding this issue:

This is the output of `sudo -u clamav stat /raid/Share/Public/`

```
root@uhs:/raid/Share/Public# sudo -u clamav stat /raid/Share/Public/
  File: `/raid/Share/Public/'
  Size: 6           Blocks: 0          IO Block: 4096   directory
Device: 900h/2304d  Inode: 54526208    Links: 2
Access: (0777/drwxrwxrwx)  Uid: ( 1000/awensley)   Gid: (  120/   admin)
Access: 2011-01-19 01:00:00.304365306 -0600
Modify: 2011-01-18 22:47:06.793592673 -0600
Change: 2011-01-19 00:42:52.023813550 -0600
root@uhs:/raid/Share/Public#
```

---

### Post by James78 on 2011-01-19
*"One of the differences between clamscan and clamdscan is that clamscan runs as the user requesting it whereas clamdscan runs as a special user (usually clamd, I believe), which would be in a special administrative category allowing it to read across multiple user's files."*
[http://www.mail-archive.com/clamav-users@lists.clamav.net/msg33470.html](http://www.mail-archive.com/clamav-users@lists.clamav.net/msg33470.html)

So, this is why a hyphen should work vs the regular way not working.

---

### Post by flamadiddle on 2011-01-19
Thanks for that info, James78.

I understand the difference between the hyphen usage and normal usage.  I need to make the normal usage work so that the daemon can scan directories.

The clamav daemon is running under the user 'clamav' and that user is in both the 'root' and 'admin' groups.  The directory being scanned has 777 permissions.  So either I'm missing something really obvious or there's more going on than the normal user/permissions FAQ can fix. :-(

---

### Post by flamadiddle on 2011-01-19
Double post, sorry.

---

### Post by flamadiddle on 2011-01-24
I have [[COLOR="Blue"]_posted this question on Ask Ubuntu_[/COLOR]]("http://askubuntu.com/questions/22307/clamdscan-lstat-failed-permission-denied-error") and offer a 50+ reputation bounty if anyone is a member of that site.

I will accept any advice, but **_I need to scan whole directories recursively with clamdscan_**.

---

### Post by flamadiddle on 2011-01-26
After some help on AskUbuntu.com, I've concluded that this is a bug.

I've filed a [[COLOR="Blue"]_bug report on Launchpad_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/708395").

---

