---
title: "Backup solution for local Debian install"
date: 2010-01-23
forum: General Help
---

### Post by youoneah on 2010-01-23
I manage two machines at home that each multi-boot Vista, Debian, and Ubuntu. I have to admit I was never very careful with backing up, but experience is a good teacher. I plan to upgrade Debian to testing, but want a backup solution planned that will allow me to restore to the last stable state. This doesn't have to be a bare-metal backup, but it does need to preserve the file structure and permissions. For my desktop, this is a single partition with ReiserFS.

This is no problem with a live CD like Clonezilla or Partimage, but I rather prefer taking advantage of the multi-boot setup: why not backup up Debian from Ubuntu while doing other (low hard-drive access) tasks? A bit more fun than the single-purpose interface of a live backup CD.

I've no experience doing this without a live CD. Would something like tar/gzip or rsync be sufficient? What tools are available? Any tips on recent problems? For instance, I noted from the [Mondo community docs]("https://help.ubuntu.com/community/MondoMindi") that Mondo has had problems, but the tools have had updates since then.

---

### Post by labinnsw on 2010-01-24
[ATTACH]144801[/ATTACH]

Alter the attached instructions to suit your needs.
Substitute your alternate OS wherever you see Live CD.

Adopted from: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by youoneah on 2010-02-06
Hey thanks, this looks useable.

I ended up going with Clonezilla just to be sure, but in the end didn't need it as the upgrade went well.

---

### Post by Barriehie on 2010-02-08
Here's another one, edit to your specs.  This backs up $HOME and /etc to an external drive and also gets a list of installed packages.  When that's done it copies those files out to a USB stick and changes the owner:group attributes to user instead of root.

Barrie

```

#!/bin/bash
#

#
#  Find and remove  emacs backup files.
#
find / -iname *~ -user barrie -exec rm {} \;

#
#  Remove the thumbnails.
#
#find /home/barrie -name .thumbnails -exec rm -rf {} \;

#
#  Remove Thunar sessions
#
rm /home/barrie/.cache/sessions/Thunar*

#
#  Nuke the Nautilus sessions
#  Leave 1 session files
#
# Specify the target directory and file names to operate on.
target_files=~/.nautilus/saved-session-*

# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=1

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi

#
#  Nuke the Metacity sessions
#  Leave 1 session
#
# Specify the target directory and file names to operate on.
target_files=~/.metacity/*

# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=1

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi

#
#  Do the Backup
#
BUPFILENAME=bup$(date +%m%d%y).tgz
#INSTALLEDFILEZ="/home/barrie/Documents/"$(date +%m%d%y)-Installed_Packages.txt
dpkg --get-selections > /home/barrie/disk/backup-files/"Packages-"$(date +%m%d%y)

tar cvpzf /home/barrie/disk/backup-files/home-$BUPFILENAME --exclude=/home/barrie/Desktop/backup.log --exclude=/home/barrie/disk --exclude=/home/barrie/windoze /home/barrie

tar cvpzf /home/barrie/disk/backup-files/etc-$BUPFILENAME /etc

rm /media/disk/*.tgz
rm /media/disk/Packag*

cp /home/barrie/disk/backup-files/etc-$BUPFILENAME /media/disk/
cp /home/barrie/disk/backup-files/home-$BUPFILENAME /media/disk/
cp /home/barrie/disk/backup-files/Packages-$(date +%m%d%y) /media/disk/


chown barrie:barrie /home/barrie/disk/backup-files/"home-"$BUPFILENAME
chgrp barrie /home/barrie/disk/backup-files/"home-"$BUPFILENAME

chown barrie:barrie /home/barrie/disk/backup-files/"etc-"$BUPFILENAME-etc
chgrp barrie /home/barrie/disk/backup-files/"etc-"$BUPFILENAME-etc

chown barrie:barrie /media/disk/*.tgz
chown barrie:barrie /media/disk/Packages*
chown barrie:barrie /home/barrie/disk/backup-files/*.tgz
chown barrie:barrie /home/barrie/disk/backup-file/Packages*


exit 0

```

---

### Post by jamesr on 2010-02-13
Hi,

I personally use Mondo , and yes there were problems and one of those people reporting problems was me. But now I have solved by backing up to a local USB drive instead of the CDRW drive. I am not sure exactly what caused the problem but occured with one of the updates (running 8.04 LTS). I think mondo was finding the errors because I always did, the verify option, and it was failing. I have changed the CD burner hardware and used different blanks, and basically found that CDRW route was unreliable whereas the local USB drive route to generate ISO's and then burning these on a windows system worked. The reliabilty on the CDRW route was also variable if I burnt on the local system using Brasero, versus gnomebaker, gnomebaker being more reliable. But not reliable enough when I wanted a bare metal recovery.

---

