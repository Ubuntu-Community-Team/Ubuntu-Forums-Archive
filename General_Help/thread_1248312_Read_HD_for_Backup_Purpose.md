---
title: "Read HD for Backup Purpose"
date: 2009-08-24
forum: General Help
---

### Post by wpsd on 2009-08-24
Is there any script that can read mount point for a portable storage by their vendor and product id

I already know the vendor and product id of the storage but now I need to find where they mounted to ?

It's about backing up actually
So once in the week the IT guy will bring a portable storage for backup purpose than plug it in the server

After plugging in the script will start onplug and check whether this harddisk is for backup purpose or not ? If not do nothing;

If yes find where the harddisk mount to (e.g /media/backup /dev/backup etc ) if the harddisk is not mounted than mount to specific address

Do the backup process using rsync or just copy the folder

unmount the harddisk

I'm stuck on the first part , I don't know how to get the mount point automatically , there is a way to bypass this using FTP but the file that I'm going to backup is bigger than 10G and my internet here rather slow. and second they want to keep the portable backup harddisk in another place not in the office where the server kept, so RAID is out also.

Do you know how ? or is there any other way to solve this case ?

it's ok if it has to be in bash shell

and actually i planning to do this in CentOS but lets solve this in Ubuntu first

---

