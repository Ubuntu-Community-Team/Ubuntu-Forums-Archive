---
title: "bash help: check if cd is blank"
date: 2011-08-20
forum: General Help
---

### Post by whatthefunk on 2011-08-20
Hi all.  Im working on my bash script to backup my system.  I want to include the cd writing process in it but cant figure out how to get the system to check whether or not the inserted cd is blank.  Im using wodim to blank and write the cd.  Any help would be greatly appreciated.

---

### Post by whatthefunk on 2011-08-20
After a few hours of messing around, Ive come up with this crappy bash script which seems to do the job:

```
#!/bin/bash

##### Tests if there is a CD in the drive and whether or not it is blank ####

cd_test ()              #Tests if there is a CD in the drive
{
if wodim -atip | grep -q "Disk type"; then
  echo "There is a CD in the drive"
else
  echo "There is no CD in the drive"
  exit
fi
}

blank_test ()           #Tests if the CD is blank
{
if mount | grep -q "/dev/sr0"; then
  echo "CD is not blank"
else
  echo "CD is blank!"
fi
}

##### Main #####

sudo umount /dev/cdrom
cd_test
sudo mount /dev/scd0 /media/cdrom
blank_test
exit
```

Any recommendations on how to improve this would be much appreciated.

---

### Post by scottstensland on 2011-08-20
that's gonna be a TON of cd/dvd - if you have an external hard drive try this :

sudo  rsync  --archive   --one-file-system   /     /media/500_meg_external

is a one-liner to backup entire machine to external drive
you will first have to mount the external drive 
which is only a couple of lines

---

