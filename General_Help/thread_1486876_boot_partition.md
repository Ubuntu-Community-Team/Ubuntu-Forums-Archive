---
title: "boot partition"
date: 2010-05-18
forum: General Help
---

### Post by pcura on 2010-05-18
Hello all,

I tried installing Kubuntu with Windows XP last night, its causing some problems, but will try to re-install again tonight from scratch. My questions are:

1. Do you really need a /boot partition? (I know to do a manual partition you actually need only 3 - /, /home, and swap area)

2. Would it benefit me to have a /boot partition or would it benefit me without it? I'm thinking that the reason for having a separate partition for /boot is if your going to have a third OS. Am i right on this one?

3. I have a second hard drive (physical) that I want to make a drive for my media (for XP and Kubuntu). Would I format this with Kubuntu or XP? I was able to format it with XP but after installation of kubuntu I could not see it. If I try to format it on Kubuntu there is no NTFS only fat 16 and fat 32 which I think it would not work because its 500GB. 

thanks in advance

My computer specs are:

amd phenom II x4 with biostar mobo
1 TB hard drive (already partitioned in half)
1 500GB hard drive
4 GB RAM

---

### Post by oldfred on 2010-05-18
You do not need a separate boot partition unless you have a really old computer that has BIOS limits that force you to have the boot files at the beginning of the hard drive. Or the new partition type GPT that needs a BIOS_boot partition (for just part of grub) used for Macs, servers and all drives over 2TB as MBR only goes to 2TiB.

You cannot share a boot partition with other systems. Versions conflict and you have real problems. Some systems require a boot partition but then you have to have one for each system so boot files are unique.

If you are planning multiple installs you may not want to share /home either. You can share data but sometimes the settings in /home may conflict due to different versions of software.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by jbrown96 on 2010-05-18
The only advantage to using a separate /boot partition is if Grub does not support the file system of /. Ubuntu doesn't have any file systems that are unsupported, so there's no need for /boot. 
You could possibly make an argument on a server, but I don't think that's what you are doing. 

With 4GB of ram you don't need swap either, unless you will be using hibernate (suspend to disk), but sleep (suspend to ram), which is far more commonly used, does not need swap.

It's usually the easiest to format the media drive during Ubuntu install that way it's automatically mounted every time you boot in Ubuntu. I would use NTFS for it.

I've never had problems with a shared /home.

---

### Post by pcura on 2010-05-18
How will kubuntu see the second hard drive though? During install it does see the second hard drive but after install it only see one hard drive (1TB)? for some reason the other hard drive disappears (500GB).

---

### Post by jbrown96 on 2010-05-18
> **pcura said:**
> How will kubuntu see the second hard drive though? During install it does see the second hard drive but after install it only see one hard drive (1TB)? for some reason the other hard drive disappears (500GB).

What do you mean "disappears?" Is it not mounted, not physically recognized, not on the desktop, etc?

What does ```
sudo fdisk -l && mount -l
``` output?

---

### Post by srs5694 on 2010-05-18
> **oldfred said:**
> You do not need a separate boot partition unless you have a really old computer that has BIOS limits that force you to have the boot files at the beginning of the hard drive.

Actually, there are several other reasons, including use of LVM or RAID along with the GRUB Legacy or LILO boot loader (GRUB 2 is supposed to be able to read Linux LVM and RAID setups, but I've never tested this myself); use of a filesystem on root (/) that the boot loader can't parse; and perhaps a few other exotic things I can't recall offhand.

> **oldfred]Or the new partition type GPT that needs a BIOS_boot partition (for just part of grub) used for Macs, servers and all drives over 2TB as MBR only goes to 2TiB.[/quote]

The BIOS Boot Partition in GPT is entirely unrelated to a Linux /boot partition. Check [http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition) for a description of what a BIOS Boot Partition is. Basically, it's a place for GRUB to put part of its boot code so that it can be easily accessed without the use of filesystem drivers. The Linux /boot partition, OTOH, is a regular Linux directory in which certain types of files -- most notably the kernel, the initial RAM disk, and GRUB configuration files -- reside.

> You cannot share a boot partition with other systems. Versions conflict and you have real problems. Some systems require a boot partition but then you have to have one for each system so boot files are unique.

I disagree with this assessment. I've shared /boot partitions between Linux versions in the past with no problems. Most distributions name their kernels and other critical files different things, so there's little room for conflict. The biggest potential for conflict is in GRUB configurations. One distribution may try to overwrite the others' GRUB configuration files. This can result in unexpected and unwelcome changes to the GRUB boot menu the next time you reboot.

That said, it's been a while since I've shared a /boot partition between distributions said:**
> If you are planning multiple installs you may not want to share /home either. You can share data but sometimes the settings in /home may conflict due to different versions of software.

I strongly disagree with this. Although it's true that user configuration files can conflict between distributions, those files go in users' home directories, which are *subdirectories* of /home. That is, your user home directory might be /home/fred or /home/sally. This means that you can easily and safely share a /home partition between distributions simply by using different usernames, or even by using the same username but specifying different user home directories.

The advantage of sharing a /home partition is that you can make it as large as is desired to hold all your files. If you split things up, you'll either have to make each /home partition small enough that you may have to carefully split up your files or you'll have to create some other shared-data partition -- in which case, why not just make /home the shared-data partition? It's a simpler and more elegant solution.

[quote=pcura]How will kubuntu see the second hard drive though? During install it  does see the second hard drive but after install it only see one hard  drive (1TB)? for some reason the other hard drive disappears (500GB).[/quote]

Probably your second drive is simply not being mounted, or if it is being mounted, you don't know what its mount point is. Try posting the output of the following two commands, typed at a Linux text-mode command prompt, between [noparse]> [/noparse] and [noparse][/noparse] strings:

```

sudo fdisk -l
df -h

```

This will let us see how your system is configured and what's currently mounted.

Alternatively, you could peruse your menus for options related to mounting partitions. (I don't use the usual Ubuntu GNOME setup, so I don't recall exactly where these options are.)

---

