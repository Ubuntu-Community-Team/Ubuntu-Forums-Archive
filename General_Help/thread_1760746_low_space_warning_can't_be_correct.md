---
title: "low space warning can't be correct"
date: 2011-05-17
forum: General Help
---

### Post by camsoupa on 2011-05-17
I am running a laptop with a windows partition and a ubuntu partition.
I partitioned from windows, then setup the linux partition from the ubuntu cd and formatted it to ext4.
I am running the Ubuntu 11.0.4 and Windows 7.

PROBLEM: All reports indicate that the Ubuntu /home directory is eating 66 GB when there is no indication that is using even a fraction of that space.  

What can I do to reclaim the space?

Here is the report on the disks and usage:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32286323

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS
/dev/sda3            1926       28715   215186776    7  HPFS/NTFS
/dev/sda4           28715       38914    81920001    5  Extended
/dev/sda5           28715       38418    77934592   83  Linux
/dev/sda6           38418       38914     3984384   82  Linux swap / Solaris
cam@cam-Inspiron-1564:~$ sudo du -hx --max-depth 1 /
4.0K    /cdrom
du: cannot access `/home/cam/.gvfs': Permission denied
66G    /home
0    /sys
189M    /lib
8.0M    /bin
44K    /root
4.0K    /media
4.0K    /selinux
14M    /etc
12M    /lib32
16K    /lost+found
8.8M    /sbin
0    /proc
4.0K    /opt
743M    /var
0    /dev
23M    /boot
4.0K    /mnt
4.0K    /srv
60K    /tmp
2.4G    /usr
70G    /
cam@cam-Inspiron-1564:~$ du -hx --max-depth 2 /home
0    /home/cam/.gvfs
68K    /home/cam/.gnome2
4.0K    /home/cam/Documents
24K    /home/cam/.compiz
16K    /home/cam/.gegl-0.0
128K    /home/cam/.config
25M    /home/cam/.thumbnails
4.0K    /home/cam/.gnome2_private
4.0K    /home/cam/Templates
49M    /home/cam/workspace
4.0K    /home/cam/IDEs
4.0K    /home/cam/Videos
88M    /home/cam/Downloads
1.1M    /home/cam/.libreoffice
35M    /home/cam/.eclipse
12K    /home/cam/.mission-control
4.0K    /home/cam/.icons
124K    /home/cam/temp
57M    /home/cam/Desktop
24K    /home/cam/.ssh
422M    /home/cam/redneckracer
4.0K    /home/cam/.themes
48K    /home/cam/.fontconfig
4.0K    /home/cam/Public
12K    /home/cam/.dbus
4.0K    /home/cam/.nautilus
8.0K    /home/cam/.qt
95M    /home/cam/.android
4.0K    /home/cam/Music
4.0K    /home/cam/Pictures
1.6M    /home/cam/.gconf
24K    /home/cam/.ddd
20M    /home/cam/.cache
36K    /home/cam/.pki
1.5G    /home/cam/Android
228M    /home/cam/.mozilla
64K    /home/cam/.gconfd
4.0K    /home/cam/.shotwell
456K    /home/cam/.gimp-2.6
167M    /home/cam/src
40K    /home/cam/getlibs-all
148K    /home/cam/.pulse
4.5M    /home/cam/.local
360K    /home/cam/.gstreamer-0.10
66G    /home/cam
66G    /home

```

---

### Post by r-senior on 2011-05-17
If you want to see where space is going in your home folder, try this du command instead:

```

$ du -sm .[!.]* * | sort -rn

```

As you have it, you aren't summarising sub-directory contents (the -s option).

Or you can use Disk Usage Analyser and scan your /home directory, which will give a graphical display.

---

### Post by oldfred on 2011-05-17
Are you mounting or linking your NTFS partitions into /home? It may add all the mounts also.

---

### Post by r-senior on 2011-05-17
Well spotted, OP probably needs the -x option too.

---

### Post by camsoupa on 2011-05-17
> **r-senior said:**
> If you want to see where space is going in your home folder, try this du command instead:

```

$ du -sm .[!.]* * | sort -rn

```As you have it, you aren't summarising sub-directory contents (the -s option).

Or you can use Disk Usage Analyser and scan your /home directory, which will give a graphical display.
Thanks for the tip.  That command led me right to the problem.

It turned out that ".xsession-error.old" in /home was the culprit.  If I understand correctly this file is a log which can be become quite large if there are race conditions or something, especially if you use hibernate often and do not do a full system shut down?

---

### Post by camsoupa on 2011-05-17
To anyone else with this problem, here's a related forum on the same subject:

[http://kubuntuforums.net/forums/index.php?topic=3113581](http://kubuntuforums.net/forums/index.php?topic=3113581)

Thanks for the help!

---

