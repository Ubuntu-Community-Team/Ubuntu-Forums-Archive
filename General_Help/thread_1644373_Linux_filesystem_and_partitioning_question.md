---
title: "Linux filesystem and partitioning question ?"
date: 2010-12-13
forum: General Help
---

### Post by drdigital on 2010-12-13
Hello All,. ..

I have a question:
In Windows , I open MyComputer and see some partitions c,d,e and so

I know in Linux every thing is folder or file and all are under root. and i know I can mount different sizes to different mount points.

The problem is : Even I made another /data mount point 13 GB, I still open my File system and see a lot of folders that i do not need frequently. I want to know how to well organize this issue and keep my data in a separate part which can be accessed directly from outside the partition.

I have other partitions FAT32 and NTFS but when I store some programming projects ob them I can not build the projects (eclipse) until I move this project to the home directory or so .


How can I solve this ?????????

Thanks in advance.

---

### Post by ajgreeny on 2010-12-13
The simple answer is that you might not be able to do exactly what you want to do.

The linux operating system is very dependent on a system of permissions which are only enabled in linux filesystems, such as ext2, ext3, ext4, not in data partitions, if they are ntfs.  Such partitions will only be useful for storage of files.

From ubuntu can you please run ```
sudo fdisk -l
```(lower case L at the end, not 1), and copy back the output from that here.  It would also help to see your /etc/fstab file, or if you don't use that to mount the partitions, the output of ```
mount
```when you have mounted all the partitions that you use in ubuntu, using manual mount commands if necessary.

---

### Post by drdigital on 2010-12-13
Thanks for your replay.

[HTML]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6119    49150836    7  HPFS/NTFS
/dev/sda2           10983       38914   224354305    5  Extended
/dev/sda3            6120       10983    39062528   83  Linux
/dev/sda5           19378       38914   156923048    7  HPFS/NTFS
/dev/sda6           10983       11712     5858304   82  Linux swap / Solaris
/dev/sda7           13293       19377    48875520    b  W95 FAT32
/dev/sda8           11712       13293    12694528   83  Linux
[/HTML]

/etc/stab

[HTML]proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=38c1eab0-81a7-4c49-b2a2-22972b30e0c0 /               ext4    errors=remount-ro 0       1
UUID=632b9515-b2f6-495e-9544-8f10f85c0d90 /Data           ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0[/HTML]

---

### Post by drdigital on 2010-12-13
another question if u do not  mind,

when i open users and groups from System->Admin.
I saw the windows with dimmed option and wait long time without getting the options available . what is that ???

[IMG]http://img816.imageshack.us/img816/9320/screenshotyv.png[/IMG]

---

### Post by ajgreeny on 2010-12-13
There are no users showing in the left hand pane of your users window, so there is nothing that can be set or changed.  On my system, I appear as my username, and the window moves from greyed out to standard view very quickly.

As to your partitions, you appear to have a 40GB approx sda3 primary and 12GB approx sda8 logical partition.  I think any programming folders you need to use in ubuntu will have to be in either of those two, preferably the one with the OS on it, (sda3?).

---

### Post by drdigital on 2010-12-14
Thank You.

---

### Post by srs5694 on 2010-12-15
> **drdigital said:**
> The problem is : Even I made another /data mount point 13 GB, I still open my File system and see a lot of folders that i do not need frequently. I want to know how to well organize this issue and keep my data in a separate part which can be accessed directly from outside the partition.[/url]

It's unclear to me what you're saying. Specifically:


[list]
[*]Have you created a new partition and mounted it at /data, have you just created a /data directory, or something else?
[*]Where are these "folders that [you] do not need"? In /data? What precisely are they? Show us a screen shot or the output of "ls" on the directory in question.
[/list]


[quote]I have other partitions FAT32 and NTFS but when I store some programming projects ob them I can not build the projects (eclipse) until I move this project to the home directory or so .

This could be a question of permissions in the FAT or NTFS partition, in which case changing mount options might help. I don't know offhand how the GNOME automounter works, but you might be able to adjust mount options in /etc/fstab, if that's how you're mounting the partition(s), in order to get ownership or write access to the files in question. It's also possible that eclipse requires filesystem features that just aren't supported by FAT or NTFS (such as the ability to create symbolic links). If that's the case, there simply is no fix within FAT or NTFS. (I'm not familiar with eclipse, so I don't know what its needs are.)

---

