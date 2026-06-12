---
title: "Mount drives automatically at startup:error nautilus"
date: 2010-01-29
forum: General Help
---

### Post by Winalways on 2010-01-29
Hello everybody!

I am a new user to Ubuntu with no programming background. I use dual-boot Windows XP and Ubuntu 9.10 in two separate HDD in same PC. As Ubuntu required password for mounting each and every drive every time I created folders by name of all my drives in /root/media and made necessary editing in etc/fstab with the help of a friend. We expected ubuntu to mount all the disk partitions automatically during startup. But it has not been the case. So after starting up each time I have to go to terminal and key in [CENTER][/CENTER]sudo nautilus
Then all the drives mount automatically at one go but before that following error appears. Does this error have anything to do with my problem.
(nautilus:1969): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:1969): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1969): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1969): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by raktarok on 2010-01-29
Hi,

Can you please post the contents of your /etc/fstab file?

Also, is it correct that nautilus is not auto started when you login? Do you see icons (any icons) in the desktop when you login? (nautilus handles the desktop) As soon as you login, run this to see if nautilus is running.

```
ps aux | grep nautilus
```

The above error seems to be unrelated to this mounting issue, but sorry, I don't know how to get rid of that. It says something about enabling user sharing, but I have no idea how to do that. Anyway, the error should not pose much of a problem...

Also, remember to use gksudo instead of sudo, when dealing with graphical apps. 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jamesisin on 2010-01-31
I have written a post on adding new drives to Ubuntu.  My guess here is that you are running into a permissions issue, but you'll want to go over these instructions to make sure that you have done it all correctly.

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

Let me know if you have questions (here or there).

Also, what kinds of Samba shares have you created?

---

### Post by Winalways on 2010-02-05
Dear raktarok,

I cannot see any icons in my desktop. Also when i ran the code you provided i got the following output.

winalways   2408  2.0  1.3 190716 35768 ?        Sl   14:54   0:03 nautilus --sm-client-id 101a319d1b610c000126495291800000016010009 --sm-client-state-file /home/winalways/.config/session-state/nautilus-1265361800.desktop
winalways   2736  0.0  0.0   3040   768 pts/1    R+   14:57   0:00 grep --color=auto nautilus

Unfortunately i cannot make out anything from this. Also for your perusal i am attaching a screenshot of the error which i get when i try mounting any drive.

Also the contents of my fstab file are
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4f729454-366d-4277-84bd-a8889130a584 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=535828f0-bfc6-4d2e-8086-d34dfc2ec780 none            swap    sw              0       0
/dev/sdb1        /media/partition1        ntfs        noauto,user,exec        0        0
/dev/sdb2        /media/partition2        ntfs        noauto,user,exec        0        0
/dev/sdb3        /media/partition3        ntfs        noauto,user,exec        0        0
/dev/sdb5        /media/partition4        ntfs        noauto,user,exec        0        0
/dev/sdb6        /media/partition5        ntfs        noauto,user,exec        0        0
/dev/sda2        /media/partition6        ntfs        noauto,user,exec        0        0
/dev/sda3        /media/partition7        ntfs        noauto,user,exec        0        0

Please note that actual drive names are in place of word 'partition' in the actual file. Same thing is reflected in the screenshot too.

Regards,

winalways

---

### Post by Morbius1 on 2010-02-05
Let's take one example:
> /dev/sdb1        /media/partition1        ntfs        noauto,user,exec        0        0Change it to:
> /dev/sdb1        /media/partition1      ntfs defaults,nls=utf8        0        0Then:

Open **Terminal**
Type **sudo mount -a**

Now go to /media/partition1 and see if you can access files.

---

### Post by Winalways on 2010-02-05
Hello everybody!

Thanks everyone and specially Morbius1 for trying to solve my problem.

Now I edited my fstab file from
```
/dev/sdb1 /media/partition1 ntfs noauto,user,exec 0 0
```to 

```
/dev/sdb1        /media/partition1      ntfs        defaults        0        0
```Now all my drives mount automatically after I turn on my PC.I found this page useful along with the tip from Morbius1 which provided me a new direction  to go ahead with.

Web Page link:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by jamesisin on 2010-02-05
Great news.

Two things.  First, you will want to mark your thread as SOVED in Thread Tools above.

Also, it is usually preferred to use UUID's rather than the /dev/ designation (since the /dev/ designation can change).

---

