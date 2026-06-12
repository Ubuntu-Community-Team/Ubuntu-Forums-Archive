---
title: "Mystery Disk Consumption"
date: 2011-09-12
forum: General Help
---

### Post by linux_luser on 2011-09-12
Hello All.

v10.04, 139Gb drive fills up about once per week.  Its an enterprise level box and I can't figure out what's filling it up.  The way I clean it out now is to reboot Sunday nights.

Sum of all things on my disk: ~30G
Ubuntu's report of my disk usage: 108G

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             129G  108G   15G  89% /
none                   40G  224K   40G   1% /dev
none                   40G  164K   40G   1% /dev/shm
none                   40G   96K   40G   1% /var/run
none                   40G     0   40G   0% /var/lock
none                   40G     0   40G   0% /lib/init/rw
none                  129G  108G   15G  89% /var/lib/ureadahead/debugfs

du -sh /*

7.8M    /bin
34M     /boot
4.0K    /cdrom
388K    /dev
16M     /etc
22G     /home
0       /initrd.img
0       /initrd.img.old
273M    /lib
13M     /lib32
0       /lib64
16K     /lost+found
4.0K    /media
4.0K    /mnt
43M     /opt
du: cannot access `/proc/9974/task/9974/fd/4': No such file or directory
du: cannot access `/proc/9974/task/9974/fdinfo/4': No such file or directory
du: cannot access `/proc/9974/fd/4': No such file or directory
du: cannot access `/proc/9974/fdinfo/4': No such file or directory
0       /proc
492M    /root
8.3M    /sbin
4.0K    /selinux
200K    /srv
0       /sys
332K    /tmp
2.4G    /usr
1.5G    /var
0       /vmlinuz
0       /vmlinuz.old

Guys, any light you could shed would be greatly appreciated.  Let me know if I can provide any more info.

-Grant

---

### Post by Wim Sturkenboom on 2011-09-12
**df** is not disk usage; it reports free space which is NOT the same ;) If a deleted file is still in use by an application, it is still seen be df and subtracted from the free disk space.

**du** reports the usage and it will immediately see when a file is deleted. 

So far the difference. A reboot will stop all applications so initially no files are in use by applications and therefore df will no longer see them.

You can find which application has deleted files in use with the *_lsof_* command;from the head:
```

lsof |grep -i deleted

```

Once you know which files are still in use by which application, you can look at the cause.


PS What I'm still curious about is who looks at what :confused:

---

### Post by linux_luser on 2011-09-12
Thanks Wim!!!

I have a bunch of heavy processes running on this box and I was able to use the lsof to narrow down which ones were hoarding my disk.

---

### Post by Wim Sturkenboom on 2011-09-13
Good; please mark your thread as solved using the thread tools just above the first post on this page.

---

