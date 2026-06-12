---
title: "ntfs Fuse not working"
date: 2006-06-02
forum: General Help
---

### Post by ghee22 on 2006-06-02
Using instructions for [https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse), I was unable to do the following step successfully:
4) Try creating a new file in it, for example:

bash:~$ sudo dmesg > /media/hda1/my_dmesg_log.txt

With this, you should have now access to editing, deleting and creating files on the 

I was, however, able to write a file by doing the following:
sudo nautilus
right-click, create blank file this_is_a_test.txt
double click it, write in does this work?
save, exit
sudo tail /media/windows/this_is_a_test.txt

this would give me the correct output "does this work?"

Anyone else having issues and found a solution?

Thanks,

Parag

PS:  Thanks Ubuntu for the great distro!

---

### Post by RAOF on 2006-06-02
This would suggest that your mount options are not correct - specifically, the permissions you give to read/write to the NTFS partition.  Are you sure you added the "-o umask=0007"? to the end of your ntfsmount command?

---

### Post by der_joachim on 2006-06-02
Same here. Furthermore, after adding a line to /etc/fstab with the correct mount point and GID, it will not mount automatically. When trying to manually remount everything, I get the following message:

```
mount: unknown filesystem type 'ntfs-fuse'
```

Stranger and stranger. :???:

---

### Post by ghee22 on 2006-06-02
[QUOTE=RAOF]This would suggest that your mount options are not correct - specifically, the permissions you give to read/write to the NTFS partition.  Are you sure you added the "-o umask=0007"? to the end of your ntfsmount command?[/QUOTE]
Yes, I am sure.  I have verified this in my /etc/fstab.  Very quirky.  Before I abandon this and try the other method (the windows wrapper), I'd like to hear from someone who's followed the exact steps with it working.

note:  My /dev/hda1 wasn't hda, it was sda

---

### Post by jet87 on 2006-06-02
The problem I'm having seems to be with Ubuntu recognizing my NTFS partition after editing /etc/fstab. It seems as if the ntfs-fuse partition type that the wiki page says to use isn't recognized.  I find that strange because I'm able to use ntfsmount under sudo and write to the drive.  Is there a broken link somewhere?

---

### Post by der_joachim on 2006-06-03
Hmmm... After reading [the Fuse Wiki]("http://wiki.linux-ntfs.org/doku.php?id=ntfsmount") I am not sure that it is really ready for everyday use. :( 

I'll just stick with read-only, thank you.

---

### Post by der_joachim on 2006-06-04
OK, the solution was in [this HOWTO ]("http://ubuntuforums.org/showthread.php?t=142481") all along:

[QUOTE=LKRaider]
 5 - Fix Dapper bug #29865 of the linux-ntfs package:
```

    bash:~$ sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

```   

[/QUOTE]

That is AFTER adding users to the NTFS group! Thank you LKRaider.:mrgreen:

---

### Post by Mar7y on 2006-08-10
u might add, that there's not necessarily an /sbin/mount.ntfs-fuse like in my case. 
Look, i'm a total noob so it took me a few minutes to realize that if there is _no_ /sbin/mount.ntfs-fuse the whole command wont work.
For everybody who experiences an error, try the command without the rm:
```
sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
```

---

