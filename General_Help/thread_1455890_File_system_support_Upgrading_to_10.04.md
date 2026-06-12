---
title: "File system support/ Upgrading to 10.04"
date: 2010-04-16
forum: General Help
---

### Post by jlubey on 2010-04-16
please forgive my complete ignorance, i have a few questions here.
I am currently running Kubuntu 9.1, quite happily (triple booting macbook with snow leopard and Windows 7). I would like to upgrade to Ubuntu 10.04, but I have a few questions first.
Correct me if I am wrong, but Kubuntu is just Ubuntu with the K Desktop Environment, no? So if I were to wipe my partition and install Ubuntu 10.04, I could then install the K Desktop Environment and have Kubuntu 10.04? (sudo apt-get install)
Second question... (the real noob)
I have been trying to find a way to ¨see¨ my kubuntu partition while booted into either mac osx or windows. My kubuntu is currently using the ext4 filesystem though, and there are no drivers to make this work... Is it possible to install Kubuntu onto a filesystem other than ext2/3/4? Ideally I would like to install it onto NTFS, but i know in previous distros (6.1, 7.1) this was not possible. FAT 32 would work for me too,as my partition is only 15gb.
Or does anyone know of any drivers for ext4 for mac and windows?
Thank you!!

---

### Post by jlubey on 2010-04-16
ok nevermind the Kubuntu part, i found update-manager -d and its currently downloading the 10.04 beta release :D

the question of file system support still remains though. Is it possible to install onto NTFS or FAT 32 with the newer version of ubuntu?

---

### Post by dracayr on 2010-04-16
1: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
2: You should be able to use the ext2fsd driver (Windows, don't know for mac) for ext4 (ext4 is backwards compatible), but it will be accessed as an ext2 drive, so you don't have the new features of ext4. And yes, it is possible to install ubuntu on a different fs.

EDIT: since you'd have to format the disk to do so, you'd probably have to do a complete reinstall (or else backup the disk)

dracayr

---

### Post by jlubey on 2010-04-16
thanks for the reply, i appreciate it. What filesystems is ubuntu capable of being installed on?? i looked but couldnt find a list :/

i dont mind a full re-install, as i already have what i need backed up (and then i can just do an upgrade of a fresh install of 10.04)

---

### Post by dracayr on 2010-04-16
any filesystem that has a Unix permissions-system should work I guess. I can't give you a list, but I'm quite sure that there is no filesystem that has permissions and is supported by windows without installing some extra drivers. If you want to share data from your root partition with windows, use ext2/3 or reiserfs. You could also make the root partition ext4, as normal and use a seperate fat32 or NTFS partition named /home/jlubey/data that both operating systems have access to.

---

### Post by jpaugh64 on 2010-04-16
I wouldn't want to place Linux on a vfat partition (how would it handle symlinks?), but you could do something like putting your /home directory on a separate partition, possibly a FAT32 one, and then have [K]ubuntu mount it at boot-up. There must be a way to change an existing install to do this, but the only way I know how to do so is from the partition options of the installer.

If you did decide to install from an Ubuntu CD, then you could install the "kubuntu-desktop" package, and uninstall the "ubuntu-desktop package", which should (in theory) switch from Ubuntu to Kubuntu. You might also have to run "sudo apt-get autoremove" to clean up the automatically installed ubuntu-only stuff. However (at least on my box that's been "lived in" for a while now),  this would not uninstall gdm, and much more. There might be lots of extra packages laying around in that case

---

### Post by dracayr on 2010-04-16
> like putting your /home directory on a separate partition, possibly a FAT32 one
Not possible, /home needs the 3-level permission system.

---

### Post by jlubey on 2010-04-16
ok so what youre saying is that it IS possible to install onto FAT 32, but not recommended? I already have 4 partitions for my internal hard drive, i dont really want to create a fifth just for my home folder :/  I would like the entire OS and all files to be on just one partition, and fat32 would make that pretty easy as i already have drivers to see it from my other OSes. Whats so bad about FAT32 that you dont recomend it?

---

### Post by dracayr on 2010-04-16
> **jlubey said:**
> ok so what youre saying is that it IS possible to install onto FAT 32, but not recommended? I already have 4 partitions for my internal hard drive, i dont really want to create a fifth just for my home folder :/  I would like the entire OS and all files to be on just one partition, and fat32 would make that pretty easy as i already have drivers to see it from my other OSes. Whats so bad about FAT32 that you dont recomend it?
No, It's not possible, Fat32 and NTFS both Don't have any reasonable permission-system. If you don't want to make another partition (besides, I don't think more than 4 logical partitions are possible.. not sure about that, though), then the only solution I see to your problem is to install the e2fsd driver on windows (see in my 1. post).

dracayr

---

### Post by jlubey on 2010-04-16
ok thanks. Not the answer i wanted, but i appreciate it all the same :D

---

### Post by srs5694 on 2010-04-16
Linux can be installed on ext2fs, ext3fs, ext4fs, ReiserFS, JFS, XFS, Btrfs, and possibly some other more obscure filesystems. Most of these have no or limited support in Windows. Furthermore, even if there were a perfect Windows driver for a Linux filesystem, I wouldn't recommend using it to access the Linux root (/) filesystem. The issue is that a mistake in Windows (either user error or something stupid done by a program) could easily damage the Linux installation. For similar reasons, I prefer not to give Linux direct access to the Windows C: drive, at least not on a routine basis.

For data exchange or data sharing, I recommend setting up a shared-data partition. The best filesystems for this are FAT and NTFS, although FAT has problems with big files and both have quirks related to permissions and ownership under Linux. Alternatively, ext2fs or ext3fs will work, given appropriate drivers in Windows. If absolutely necessary, you could use ex2fs or ext3fs for your Linux /home directory and give Windows access to it, but that still makes me a bit nervous, since users' program configuration files go there and could easily be damaged by a driver bug or other Windows-side problem.

One more comment: There used to be a Linux filesystem driver called UMSDOS, which provided a layer atop FAT to provide the features that Linux needs to boot. Thus, it was possible to install Linux to FAT using UMSDOS. This driver wasn't maintained, though, and so it was dropped after the 2.6.11 kernel (in 2005). Prior to that date, some distributions supported direct installation to FAT via UMSDOS, although it wasn't extremely common. If you were absolutely desperate to boot Linux from FAT, you could look into running an older version of Linux in this way, but I'm hard-pressed to think of a good reason for doing this today.

---

### Post by The Cog on 2010-04-16
I confirm that it is absolutely not possible to install Linux (or the home folders) on a filesystem that doesn't support unix permissions - basically the filesystems the installer offers you.

I also understand that the windows drivers can't cope with anything other than ext2 or ext3 with small inode sizes (recent ext3 installs may not be readable). Although I was reading today some posts about a less well known windows driver that had ext3 support.

Your best approach may be to use a separate fat or ntfs partition for sharing data.

---

### Post by jlubey on 2010-04-18
thank you for all the replies, it is much appreciated!!

---

