---
title: "Live Disc Problems"
date: 2006-02-19
forum: General Help
---

### Post by SamMessing on 2006-02-19
When I try and run the Ubuntu Live Cd, everything goes smoothly until the "Detecting hardware to find CD-ROM drives" window comes up. Every time I run the live disc it gets stuck at 92%, saying its "loading module 'isofs' for 'Linux ISO 9660 filesystem'". What do I do to fix this problem?

Thanks!

---

### Post by Jedeye on 2006-02-19
not sure if there is a lot you can do but if you burned the cd you could try burning it again at a slower speed.

---

### Post by SamMessing on 2006-02-19
I tried that, and I ran into the same problem... Then I tried to boot in live-expert mode, and made it so it didn't load the module 'isofs'... this time it still became stuck at 92%, but while loading the modle 'ide-cd' for 'Linux ATAPI CD-ROM'... it seems to get stuck at 92% no matter what module it is loading...

any ideas on what to try next?

---

### Post by bascha on 2006-02-19
Have you tried this live cd in another computer?  Maybe it is a bad download..

---

### Post by Lux Perpetua on 2006-02-19
If you're not sure whether it's a bad download/burn or not, you should compute the MD5 hash of the disk image. There are free tools in Windows and Linux to do this. (Note: to compute the md5 hash of a CD, you will first need to extract the ISO image as a file and then run the md5 program on that.) After doing this, compare the MD5 value you get to the value posted for the live CD on [www.ubuntulinux.org](www.ubuntulinux.org) or the mirrors. If the values do not match, then the data is definitely corrupted. If they do match, then the data is almost certainly not corrupted.

---

### Post by SamMessing on 2006-02-20
I check the md5sums and the file is fine...

Could it be my hardware? I am using a Dell Latitude D810 laptop... is there any reason that would affect it?

---

