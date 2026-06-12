---
title: "Need help for remote backup shell script"
date: 2011-09-08
forum: General Help
---

### Post by niranjan_rao on 2011-09-08
Hi Folks,

I am trying to use TrueCrypt for my backup. All my files are backed up under directory say /media/bigdisk/backupdata. There is directory tree structure under this directory.

My goal is to create as many as TrueCrypt volumes required dynamically to fit all these files - 2GB per volume max. Ideally speaking I would like to use tar or something similar so that I can maintain directory hierarchy in the TrueCrypt volume and get original hierarchy back in case if I have to restore from these files. These TrueCrypt volumes will backed up on remote site.

So the goal is to compute the file list from backup directory until it gets closer to 2GB, make a tar file of these files and copy it to new crypt volume. Continue until all the files are copied.

Is this something doable in shell script? I don't have much experience of shell scripting, but based on whatever I have read so far, it seems to be doable. If not, I can always right Java code as I am more comfortable in Java.

If it's possible in shell script, any pointers to get started will be greatly appreciated.

Thanks for the help in advance.

---

### Post by niranjan_rao on 2011-09-09
Bump, any one please?

---

### Post by rolandrock on 2011-09-09
You could use rar.  It is available in the repositories and will split and compress your directory tree.  E.g.

rar a -m5 -v1000k -r /tmp/volumename treename

a = add to archive
-m5 = high quality compression (slow) -m0 = no compression (fast)
-v1000k = make volumes of 1000k
-r = recursively traverse directories
/tmp/volumename = prefix of volumes (rar will add suffix part1.rar part2.rar... until complete)

---

