---
title: "Ubuntu 10.04 wont boot after editing /etc/grub.d/05_debian_theme"
date: 2010-09-22
forum: General Help
---

### Post by dtmorgwsu on 2010-09-22
Hi,

I was trying to change the splash image for my grub2 boot loader. I ended following a guide for 9.10 and messed up my system. I tried cutting and pasting the original text back in, and updating grub. But now my system wont boot. It wont even boot into failsafe mode.

The grub2 boot menu shows up and it starts booting but then tells all processes to halt, and gives me the recovery console. If I go into root terminal mode I can get it to go into the desktop environment by using "startx" but even wiping grub and the updating, and reinstalling and updating doesn't seem to fix the issue.

My system is dual booting from a hybrid mbr/ active gpt.

/dev/sda1- is the efi
/dev/sda2- hybrid mbr/ XP Sp3
/dev/sda3- swap
/dev/sda4- ubuntu installation.

Is there any way to fix this?

Thank you,

dtmorgwsu

---

### Post by srs5694 on 2010-09-22
My suspicion is that your hybrid MBR has gotten messed up. Please post the output of:

```

sudo fdisk -lu /dev/sda
sudo gdisk -l /dev/sda

```

These commands, in combination, will tell us how your MBR and GPT partitions are configured.

Note that gdisk isn't installed by default. If it isn't installed on your system, either run these commands from [PartedMagic](http://partedmagic.com) or [SystemRescueCd,](http://www.sysresccd.org) which include it; or install it in your partially-booted system by using "sudo apt-get install gdisk" or by downloading the .deb package for your architecture from the GPT fdisk [Sourceforge page](http://sourceforge.net/projects/gptfdisk/files/) and installing it with dpkg.

---

### Post by dtmorgwsu on 2010-09-22
Thanks, Here is the output...

dtmorgan@dtmorgan-laptop:~$ sudo fdisk -lu
[sudo] password for dtmorgan: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f112f11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      409640   129208319    64399340    7  HPFS/NTFS


And gdisk..


dtmorgan@dtmorgan-laptop:~$ sudo gdisk /dev/sda -l
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 312581808 sectors, 149.1 GiB
Disk identifier (GUID): 00000000-0000-0000-0000-000000000000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Total free space is 15263 sectors (7.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          401624   196.1 MiB   EF02  
   2          409640       129208319   61.4 GiB    0700  Linux/Windows data
   3       308480130       312576704   2.0 GiB     8200  Linux swap
   4       129208320       308477951   85.5 GiB    0700  Linux/Windows data


I already had gdisk installed. That is how I converted it to a hybrid MBR. I also was able to get 10.04 to boot from a super grub2 disk, but I have yet to be able to figure out what the problem is.

Also if it matters I get the grub2 boot menu and can boot into Windows XP.

Thanks,

dtmorgwsu

---

### Post by srs5694 on 2010-09-23
Your partitions look OK to me, so I'm now leaning toward a suspicion that GRUB is misinstalled. In fact, I see that you do not have a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) Although GRUB 2 can usually boot without this partition, it's more reliable with such a partition in place. Since you say you can boot using a Super GRUB Disk, I recommend you boot that way, create a BIOS Boot Partition (it looks like you've got enough unpartitioned space -- it can be a pretty tiny partition), reboot again using Super GRUB Disk, and then do a "sudo grub-install /dev/sda". With any luck that'll solve the problem.

---

### Post by dtmorgwsu on 2010-09-24
When you say create a bios boot partition do you mean to create a partition and when you do check the bios_grub boot option if you gparted?

I did that the last time that I had problems with it and everything was working fine until I decided to change the 05_debian_theme.

As for booting with supergrubdisk and installing to /dev/sda...

It says it installs fine with no errors. But it still then goes back to the rescue prompts after a few screen refreshes. Is there a way to wipe grub and start over? Or would that make my system unbootable? I have also used grub2 restore utilities from the rescatux live cd, and get the error that it cannot fix grub2 installation.

---

### Post by srs5694 on 2010-09-24
> **dtmorgwsu said:**
> When you say create a bios boot partition do you mean to create a partition and when you do check the bios_grub boot option if you gparted?

Yes; however, upon reviewing your earlier posts, I see that you already have a BIOS Boot Partition (it's /dev/sda1 in the GPT scheme). Somehow that partition eluded my attention when I first looked at your gdisk output.

> I did that the last time that I had problems with it and everything was working fine until I decided to change the 05_debian_theme.

I don't really know what went wrong when you edited that file, but my suspicion is that there was something else that was the root cause of the problem -- just something that happened to coincide with that change, temporally speaking.

> As for booting with supergrubdisk and installing to /dev/sda...

It says it installs fine with no errors. But it still then goes back to the rescue prompts after a few screen refreshes. Is there a way to wipe grub and start over? Or would that make my system unbootable? I have also used grub2 restore utilities from the rescatux live cd, and get the error that it cannot fix grub2 installation.

Re-installing GRUB 2 *does* wipe it out and start over, at least in terms of the boot loader configuration.

At this point, you should probably re-install GRUB 2 (using a BIOS Boot Partition) and then run the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) which will summarize various details about how the system boots (or is supposed to boot). Post the output here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility.

Another option would be to abandon GRUB 2 for booting and go back to GRUB Legacy or LILO.

Yet another option would be to convert the disk from GPT with a hybrid MBR to a conventional MBR. (Hybrid MBRs are ugly and dangerous, and that configuration could well have something to do with the problem you're having.)

---

