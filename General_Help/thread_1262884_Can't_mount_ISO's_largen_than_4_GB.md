---
title: "Can't mount ISO's largen than 4 GB"
date: 2009-09-10
forum: General Help
---

### Post by Grps on 2009-09-10
Hello. I have downloaded a popular game by torrent and have a 7.7GB ISO but I haven't found any program able to mount it in any way. I use ubuntu 8.04 and have tried anything and everything (or so I'd like to think) from terminal mount to gisomount, kisomount, furious ISO mount, nautilus scripts/actions. Nothing seems to work.
I get the very same error every time 
> An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Now I am trying a backdoor method: installing virtualbox-ose getting a Windows XP, mounting the ISO with daemon-tools (or something), extracting the files from the iso then copying them unto ubuntu.

I'd like to have a simpler method to mount large ISO's though.



p.s.: mounting in WinXP (virtualbox) is working so the ISO is not broken. Mounting smaller ISO's than 4GB is working just fine.

p.p.s.:if there is a thread concerning this problem, I'm sorry I couldn't find it. Yes, i have searched for 2 days.

---

### Post by Bachstelze on 2009-09-10
The terminal output is useless if you don't tell us the exact command you ran.

---

### Post by Grps on 2009-09-10
Ok, now I feel stupid.



Initial problem solved. I managed to mount the ISO with
 sudo mount -o loop /path/to/iso.iso /mount/place/

and with gmount-iso....Now i feel really stupid. I tried all day and it didn't work. Nothing did... I think i can acces the ISO because i have it mounted in my virtual WinXP (don't know if that makes any difference).




The problem now is that I can't see some files that are invisible and Ctr+H doesn't work.
I know the files are invisible (and there) because I mounted the ISO in WinXP... Disk Usage Analyzer doesn't see the files either. And yes they are the bulk of the DVD. The part that is visible and accesbile is only 37mb.



L.E.: I can't open the ISO with archive manager.
> CD-ROM is NOT in ISO 9660 format

---

