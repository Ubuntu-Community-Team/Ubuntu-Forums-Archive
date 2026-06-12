---
title: "Need help with NTFS/FAT32 permissions; Programs say &quot;Permission denied&quot;"
date: 2009-06-25
forum: General Help
---

### Post by Doval on 2009-06-25
I have 3 main partitions on my hard drive: one for Windows (NTFS), one for Ubuntu (ext3), and a third I call "storage" (FAT32) in which I keep the bulk of my files so as to keep them OS-independent. In other words, I'm trying to keep as much as I can out of the Windows and Ubuntu partitions.

Now, for whatever reason, Ubuntu didn't automatically detect the Windows and Storage partitions, so I had to edit fstab using the [wiki entry](https://help.ubuntu.com/community/Fstab) as a reference. I used the following options for both the Windows and Storage partitions:```
defaults,user,dmask=000,fmask=000
```So that I could mount the partitions without being root, and so that every user had read/write/execute permissions.

I thought everything was fine, until I moved my freshly-obtained Linux emulators (Xe and pSX) over to the Storage partition. Now they won't run! Trying to run them through the command line returns this message, even if I sudo the command, and even if I log on as root using 'su'. What's going on and how can I fix this? Every permission is enabled ('ls -l' shows rwxrwxrwx on all files and folders.) The files are owned by root, yet 'sudo' and 'su' fail me. Help!

---

### Post by michy99 on 2009-06-25
If the storage partition is FAT32, it does not support linux permissions. You should use it for data only.

---

### Post by merlinus on 2009-06-25
You might try something like this in fstab for the fat partition:
[SIZE=-1][FONT=Bitstream Vera Sans Mono]
[/FONT][/SIZE][SIZE=-1][FONT=Bitstream Vera Sans Mono]/dev/hda1[/FONT][/SIZE][SIZE=-1][FONT=Bitstream Vera Sans Mono]  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0  1[/FONT][/SIZE]

---

### Post by Doval on 2009-06-26
I tried the options you mentioned, merlinus, but it still wouldn't allow me to run the programs. I guess I'll just have to follow michy's advice and stick to data storage on that partition, keep the programs elsewhere.

By the way, where can I read up on the meanings of all these dmask/fmask=xxx options?

---

### Post by merlinus on 2009-06-26
What programs are you trying to run from your fat partition?

Try google for info on umask, etc.

---

### Post by swerdna on 2009-06-26
You can't alter the permissions/ownership by using chown or chmod on mounted fat32 or ntfs partitions after the mount has occurred. The ownerships and permissions are set in concrete by the options implicit in the mount commands or if you vary the default options, then by those options. The sorts of ownerships/permissions available are shown in these two tutorials from openSUSE (just as relevant to Ubuntu):

For NTFS:
[HowTo Mount your NTFS Filesystem/Partition for Read/Write Access]("http://opensuse.swerdna.org/susentfs.html")
There's a table of umasks at the bottom of that one too FYI.

For FAT:
[HowTo mount FAT32 (VFAT) partitions with read-write access]("http://opensuse.swerdna.org/susefat32.html")

---

