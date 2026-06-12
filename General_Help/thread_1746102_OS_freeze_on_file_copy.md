---
title: "OS freeze on file copy"
date: 2011-05-01
forum: General Help
---

### Post by plo on 2011-05-01
I have a really weird issue.
Fresh install 11.04 on a HP DM1-3110eo (basically same as HP DM1z).
E-350 processor 4Gb and a 7200 / 500Gb disc.

I selected an encrypted home partition at install. Booting into Gnome.

When I copy a larger file the OS (2.3 Gb) freezes before the copy is done.
* I tried copying from a external NAS
* between two directories in my /home partition 
* and also between my /home and /tmp.
* I also copied via terminal (to exclude Gnome/X error)
All result in an OS freeze (parrtly into the copy process) = Hard reboot.

A lot of file operations work fine. I have as an example:
* Installed virtualbox (no problem)
* Created a win7 virtualmachine (and installed win7).
* I have updated all software

I have no clue where to start looking. Only thing that looks weird to me is the swap (saw the issue in the release notes) but I don't see how that could affect (and I'm not sure my swap is wrong).
I have /root, /home, /swap as separate partitions.
blkid:
[I]/dev/sda1: LABEL="SYSTEM" UUID="AAB8FFA2B8FF6AE9" TYPE="ntfs" 
/dev/sda2: UUID="cfe1b8b5-e8b5-4515-a946-126ce730a29a" TYPE="ext4" 
/dev/sda4: LABEL="HP_TOOLS" UUID="0A67-3DDE" TYPE="vfat" 
/dev/sda6: UUID="02b52873-f0f4-40c4-b072-4b00affc4c65" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="f05a2536-ffd6-4a9f-ab31-cb1245a96c85" TYPE="swap"[/I] 

"SYSTEWM" and "HP TOOLS" are HP recovery partitions that I left in there initially.

My only guess is that it has something to do with the encrypted /home, but ...????

---

