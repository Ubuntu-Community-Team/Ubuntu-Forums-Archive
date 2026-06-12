---
title: "Need help with bash script to copy files from DVDs to a hard drive"
date: 2011-11-05
forum: General Help
---

### Post by okaoka on 2011-11-05
Hi, I am trying to correct a script I want to use to automate the copy of DVDs from a cdrom to my hard drive and I just can't get it to work. 

Here it is: 

```

#!/bin/bash

mount /media/cdrom
cd /media/cdrom
cp * -r /media/cdrom /media/"Expansion Drive"/Fichiers/FR/

#eject
```

I use a similar script two or three years ago and the cdrom was named cdrom0. But now, event by changing the cdrom name, nothing work.

At the beginning of the script, I get:
*mount : impossible de trouver (not able to find) /media/cdrom/ dans /etc/fstab ou /etc/mtab*

If I look in */media*, I get this:

drwxr-xr-x 2 root    root     4096 2011-09-26 16:53 cdrom
drwx------ 1 user user  4096 2011-08-17 21:27 Expansion Drive
dr-x------ 1 user user  2048 2005-12-12 23:28 FR20051212

*cdrom* seems to be identified by Ubuntu separately from the disk *FR20051212* (volume name) itself.

I tried to find an answer on Internet but the search terms are too general to get a specific answer. 

What am I not understanding?

Thanks

Sorry if the question looks noob, but some days, I really am!

---

### Post by wojox on 2011-11-05
Try something like:

```
mount -t iso9660 /dev/scd0 /media/cdrom
```

---

### Post by okaoka on 2011-11-05
> **wojox said:**
> Try something like:

```
mount -t iso9660 /dev/scd0 /media/cdrom
```

Thank you,

It works, but it seems that I have to mount the cdrom each time I eject a DVD. Also, it shows errors like file does not exist (but finally copies it).

---

### Post by mc4man on 2011-11-05
There's nothing compelling that I've seen that says you can't use a static mountpoint & fstab entry.
If so, assuming your drive is /dev/sr0 (d. check if need be

```
sudo mkdir /media/cdrom0; gksudo gedit /etc/fstab
```

on a new line at bottom of fstab
```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0  0
```
Restart

---

### Post by okaoka on 2011-11-06
> **mc4man said:**
> There's nothing compelling that I've seen that says you can't use a static mountpoint & fstab entry.
If so, assuming your drive is /dev/sr0 (d. check if need be

```
sudo mkdir /media/cdrom0; gksudo gedit /etc/fstab
```

on a new line at bottom of fstab
```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0  0
```
Restart

Hi 

It now works.

The drive was well /dev/sr0, as I had found out yesterday.

I now have this in /media/:
drwxr-xr-x 2 root    root     4096 2011-09-26 16:53 cdrom
dr-xr-xr-x 7 root    root     2048 2007-10-18 21:54 cdrom0
drwx------ 1 user user  4096 2011-11-05 22:45 Expansion Drive

So, if I understand, cdrom and cdrom0 are just like aliases to the actual thing?

Final version of the script (It copies the files, add the files names to a list in a file on my desktop and eject the DVD:

```
#!/bin/bash
mount /media/cdrom0
#cd /media/cdrom0
volname >>~/Bureau/liste_copies.txt
ls  /media/cdrom0  >> ~/Bureau/liste_copies.txt
echo -e "--------- " >>  ~/Bureau/liste_copies.txt
cp    /media/cdrom0/* -r  /media/"Expansion Drive"/Fichiers/FR/
eject
notify-send "Copie du DVD complétée :o)"
```

Thanks a lot wojox & mc4man for your help. :D

---

