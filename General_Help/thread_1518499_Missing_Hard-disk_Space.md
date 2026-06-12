---
title: "Missing Hard-disk Space"
date: 2010-06-26
forum: General Help
---

### Post by Andrew Howe on 2010-06-26
Hi,

I am a new user of Ubuntu. I have it installed on a second partition on my second hard-disk. The partition I created for Ubuntu was 10 GB in size: 9.5 GB for the installation, 0.5 GB for swap. Today I have been getting messages warning me that I am running out of space. I ran the Disk Usage Analyser and this is what I was presented with:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161638&stc=1&d=1277584426[/IMG]


How can this be? If  ' / ' is 4.6 GB in size, how can I be using 8.1 GB of the partition, as it states in the top line? On top of this, the ext4 partition in question is 9.5 GB in size, and I have verified that using the Disk Utility, so even the filesystem capacity of 8.7 GB stated is dubious.

Can anyone shed some light on this situation?

Cheers.

---

### Post by Johnny B on 2010-06-26
run the 'df -h' command in terminal to get a more accurate analysis of your disk space. Disk usage analyzer says 'total file system capacity' not just the partition, that includes your /home and mounted disks. 

the missing disk space is due to the reserved block count, which is set to five percent by default in ext2 and ext3 file systems, I would bet its the same for ext4.

you can change the reserved block count with tune2fs, but i would not recommend using it on the root drive.
```

tune2fs -m 1 /dev/sda2
tune2fs 1.40.8 (13-Mar-2008)
Setting reserved blocks percentage to 1% (239311 blocks)
```

---

### Post by belkinsa on 2010-06-26
I been meaning to ask this, thank you poster for posting it.  But when I do the last part of what Johnny said I get this:

```
svetlana@svetlana-desktop:~$ tune2fs -m 1 /dev/sda2
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sda2
Couldn't find valid filesystem superblock.
svetlana@svetlana-desktop:~$ tune2fs 1.40.8 (13-Mar-2008)
bash: syntax error near unexpected token `('
svetlana@svetlana-desktop:~$ Setting reserved blocks percentage to 1% (239311 blocks)

```This is normal to get?

I only have 100GB less of free space and I'm not dual booting.

---

### Post by Johnny B on 2010-06-26
the second and third lines are output from the command.
you should run it as:

> sudo tune2fs -m 1 /dev/sda2
however /dev/sda2 is just an example, 'df -h' will tell you what disk labels are. ex:
> $ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2             9.9G  3.8G  5.6G  41% /
none                  3.0G  336K  3.0G   1% /dev
none                  9.9G  3.8G  5.6G  41% /var/lib/ureadahead/debugfs
/dev/sdc3              17G  4.0G   12G  26% /home


---

### Post by belkinsa on 2010-06-26
Thanks, I got it.

---

