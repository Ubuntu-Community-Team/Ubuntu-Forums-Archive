---
title: "Odd errors in rsync log Can anyone help?  Thanks in Advance..."
date: 2010-08-15
forum: General Help
---

### Post by grunge09 on 2010-08-15
I am using rsync to backup across the network from my Ubuntu machine to my freenas NAS RAID Box.  I had 10/100 switch and swapped it out for a unmanaged asus gigbit 8 port hub.  

I use CIFS and auto mount the backup server in FSTAB.  Freenas is setup with samba/cifs.  

Setup 3 users on freenas, same user group (homelan), made the same usergroup on local ubuntu pc and use GID=homelan.

My rsync cmd:

rsync -avpL  --progress --delete --log-file=/home/mom/rlog/$(date +%Y%m%d)_rsync.log /home/home /mnt/freenas/moms-pc

Error #1
rsync: mkstemp "/mnt/freenas/moms-pc/mom/Pictures/2010/01-17-2010 eBay/.FLSTS Heritage Springer 1:10 model-1.JPG.04w92H" failed: No such file or directory (2)

Now the files name ends at JPG I checked and system allows me to access the file.   There is no /.FLSTS .... its just FLSTS .... ending in JPG.  

Is rsync copying the original file to a tmp file and deleting it on the fly and then looking for it to copy and freaking out?  

Error #2

rsync: mkstemp "/mnt/freenas/moms-pc/mom/.nautilus/metafiles/.file:%2F%2F%2Fmedia%2Fdisk%2Fe-2000%2520drivers.xml.nTdD4e" failed: No such file or directory (2)

Now that is just one of the METAFILES it freaks out as.  Again is this .nTdD4e file a tmp file rsync makes that disappears on the fly?

Error #3:

Also I get mktemp errors on some /.pulse <dir> files and some /.gnome2/files.  No suck file or directory.

Should I exclude them so I do not get the errors.

---

