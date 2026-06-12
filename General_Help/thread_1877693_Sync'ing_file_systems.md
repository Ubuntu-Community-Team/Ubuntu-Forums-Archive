---
title: "Sync'ing file systems"
date: 2011-11-08
forum: General Help
---

### Post by datavirtue on 2011-11-08
I have noticed that when issuing a cp -u command to copy files to a windows share it is not able to digest the dates from the NTFS volume and therefore copies everything without comparing dates. Is there a way that I can get the cp command to recognize NTFS properties? This is extremely annoying.

11.10

Thanks for any help.

---

### Post by Roasted on 2011-11-08
I may be wrong, but I thought I remember being told when I was trying to rsync -a data from an NTFS share to an EXT share that I could not preserve a lot of the properties of the files. It's an unfortunate downside to NTFS being, well... NTFS... and it living in a Linux environment.

---

### Post by papibe on 2011-11-08
Hi datavirtue,

I think may be experiencing the [known problem]("ftp://ppp.samba.org/pub/unpacked/rsyncweb/daylight-savings.html") of DST and UTC time conversion of NTFS and FAT file systems.

I don't think 'cp' can deal with that problem, however rsync has an special option to deal with that problem:
```
--modify-window=1
```
Start as the example (value 1) and check if that solve the problem. If not maybe a bigger value may work better.

Here's are some examples on how to use rsync:

Copy entire directories:
```
rsync -av source/ destination/
```
If you run the command again it only copy the files that has been changed on source. If you also want to delete the files you deleted on source:
```
rsync -av --delete source/ destination/
```
Same thing but you have NTFS on the mix:
```
rsync -av --modify-window=1 --delete source/ destination/
```
rsync only works on one direction at a time so if you make changes on destination/ and run the command again, you'll loose your changes. However, you can pull the changes first:
```
rsync -av --modify-window=1 --update destination/ source/
```
(note the swap between destination/ and source/)

I would advice making some 'tests' before copying your real date.

Hope it helps,
Regards.


Hope it helps,
Regards.

---

### Post by blind2314 on 2011-11-08
> **datavirtue said:**
> I have noticed that when issuing a cp -u command to copy files to a windows share it is not able to digest the dates from the NTFS volume and therefore copies everything without comparing dates. Is there a way that I can get the cp command to recognize NTFS properties? This is extremely annoying.

11.10

Thanks for any help.

Nope, for what you're wanting 'cp' isn't really designed to do it. You *might* have some access with rsync, but as mentioned below, it's not really great at digesting NTFS properties either.

---

### Post by datavirtue on 2011-11-08
I will look into rsync. I'm going from extfs2 (I think) to NTFS mostly.

Thanks for the help.

---

