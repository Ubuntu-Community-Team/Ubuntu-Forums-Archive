---
title: "Files disappearing, errors during boot"
date: 2010-12-17
forum: General Help
---

### Post by hej.mich on 2010-12-17
On my laptop I've got -  Win7(ntfs), Ubuntu 10.10 x64 (ext4) and a few ntfs partitions which are also mounted under ubuntu.

1.Today when I opened console text like this appeared: "I don't know you". In Users and groups there was nothing! No users, no groups! I've rebooted PC and then it could not boot - error while mounting filesystem and cannot open password database. I've booted from Live cd, /etc/password was corrupted so I've used /etc/password- file. Linux booted successfully. On ntfs partition I've found strange files: fileX.ntfs-3g-0000000002 fileX.ntfs-3g-0000000003 ... ntfs-3g-0000000154.

2. While ago after work under linux, when I booted into Windows appeared screen with disk error checking - after scanning some files from the disk disappeared.

3. I've checked disk with a few S.M.A.R.T. checking tools - everything seems to be OK. Tool from BIOS (ThinkPad) for checking disk and disk controller found no errors.

4. While booting Ubuntu after hibernation appears errors (but it still boots):
[http://dl.dropbox.com/u/224638/IMAG0007.jpg](http://dl.dropbox.com/u/224638/IMAG0007.jpg)

---

