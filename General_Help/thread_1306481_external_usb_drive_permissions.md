---
title: "external usb drive permissions"
date: 2009-10-30
forum: General Help
---

### Post by acefromspace on 2009-10-30
I have an external usb harddrive that works fine when using ubuntu (including permissions), but when I connect it to windows (I have a scanner that is not supported by linux) then reconnect to ubuntu, the permissions have changed (I assume windows did this?) It only allows root to have privilages so I can't copy/paste files. I only use windows for the scanner, but am also worried that every time I connect it to a friends windows system this will keep happening. Big PITA! Please explain how/why this happens. I know how to remedy the permissions issue (and have to do it eveytime the drive is used with windows, then used with ubuntu), but I don't like mysteries and would like to know what's going on.

---

### Post by ottosykora on 2009-10-30
One question : how did you format it initially?

Rights: is it formated in a way that it needs rights, e.g. NTFS?

There is a formating with a switch 'nosecurity' which helps in such situations, but also old fat32 is a solution.
Often formating while connected as external helps, since then even windoews should format with 'nocecurity' by default. 
Problems are often prsent, when disk was formated as notmal disk inside a pc and then put inside some external case.

---

### Post by acefromspace on 2009-11-02
Thank you. Yes, NTFS... and yes, formatted in computer, then put in external case. By the way, if I setup dual boot (one partition windows, one shared partition for data, one partition ubuntu) instead of using the external drive, will I have similar issues? Should I use NTFS or FAT32 for shared partition? Also, I used a windows install to format the external drive (I know... stupid) I will now use ubuntu to do all formatting.
P.S. After I scan a few more rolls of film, the old film scanner goes in the trash and I will be completely windows free! It's a Pacific Image 1800 and isn't that good anyway.

---

### Post by Giblet5 on 2009-11-02
Any filesystem that Windows uses natively has either no, or very limited, file permissions.

There are mount options to override the default permissions mapping for NTFS and FAT32/16 filesystems (see the man page for mount) which you can automate from /etc/fstab as well.

---

