---
title: "Share NTFS partition between Ubuntu/ArchLinux/WinXP"
date: 2010-01-18
forum: General Help
---

### Post by akhilbehl on 2010-01-18
Hey All,

I am triple-booting the OS mentioned above. I only recently decided to try Arch. The issue however is with Arch & Ubuntu.

My hard drive contains a common swap partition for Ubuntu and Arch, the home directories of both Linux, the C: drive for WinXP and a partition called 'Share' which as the name suggests I use to keep all the files (work, music, vids etc.) that I want to share between the various OS.

Till before Arch, I could easily share files between Ubuntu and WIndows. It seems it was possible because Windows does not respect the file permission restrictions, or may be not at least the ones imposed by Ubuntu. However now that I have Arch on a partition, Arch can not read the files owned by my user on the ntfs partition. This basically blocks my access to everything on the Arch system except for the system files.

I would like to know how I can securely share my files between the too Linux. If it is advisable and also if it is secure.

For the workaround, I am not worried about using the cli, however one shall have to be patient with me since I am not a veteran at Linux.

Thanks for the help in advance.

---

### Post by michy99 on 2010-01-18
The ntfs filesystem does not support linux permissions. If you are having problems accessing the files in arch it is probably due to not mounting it correctly.

---

### Post by J V on 2010-01-18
Popular options:

1. Symlinks
2. One /home, two OS

---

### Post by michy99 on 2010-01-18
> **J V said:**
> Popular options:

1. Symlinks
2. One /home, two OS

I would not try to share one /home between Ubuntu and Arch because the different set-ups might cause conflicts. Anyway, that isn't what the poster is asking about.

---

### Post by michy99 on 2010-01-18
I found a page on mounting ntfs drives in Arch:

[http://wiki.archlinux.org/index.php/NTFS_Write_Support](http://wiki.archlinux.org/index.php/NTFS_Write_Support)

---

### Post by Morbius1 on 2010-01-18
Just so you know the ntfs filesystem driver already in the kernel allows write access so ntfs-3g is no longer needed. Been that way for a while now.

---

### Post by falconindy on 2010-01-18
> **Morbius1 said:**
> Just so you know the ntfs filesystem driver already in the kernel allows write access so ntfs-3g is no longer needed. Been that way for a while now.
Yes, it's also "been that way for a while" that you can only modify pre-existing files with the kernelspace ntfs driver. You cannot create new files.

From [linux-ntfs.org](http://www.linux-ntfs.org/doku.php?id=texteditorpitfall):
> Naturally, creating another file is not supported and the save fails.

The userland tools ntfsmount and ntfs-3g both support creation of new files but there exists no kernelspace driver that will create new files on an NTFS partition.

---

### Post by Morbius1 on 2010-01-18
> **falconindy said:**
> Yes, it's also "been that way for a while" that you can only modify pre-existing files with the kernelspace ntfs driver. You cannot create new files.
I'm easily confused but do you mean the new file I just created on my ntfs partition is impossible.

It's mounted in fstab as this:
> LABEL=BACKUP /windows/BACKUP ntfs defaults,umask=000,uid=1000,gid=46 0 0

---

### Post by michy99 on 2010-01-18
> **Morbius1 said:**
> I'm easily confused but do you mean the new file I just created on my ntfs partition is impossible.

It's mounted in fstab as this:

I bet if you check, you will find you have the ntfs-g3 package installed.

---

### Post by Morbius1 on 2010-01-18
> **michy99 said:**
> I bet if you check, you will find you have the ntfs-g3 package installed.

You are absolutely correct. Must have come that way. I stand corrected. My apologies.

I guess I was just full of ... um ... misinformation.

---

### Post by michy99 on 2010-01-18
I believe it installs by default, because I have it, and I don't even have any ntfs partitions.

---

### Post by akhilbehl on 2010-01-23
hey guys.. thanks a lot for the help..

it must then be because of not mounting it correctly as one of the users suggested. I can't even check it right now.. since my Arch fails to boot up since it can't find the root partition after an upgrade. so can only check your suggestions after this gets solved.

btw.. i know this is not the place to ask this.. but would any of you know.. a way to solve this.. i have tried using both UUID and LABEL of the partition in the fstab but nothing works. My grub-installer is in the ubuntu-partition.

---

