---
title: "Backup that spans multiple external drives"
date: 2010-08-08
forum: General Help
---

### Post by draxenato on 2010-08-08
Hi, I'm trying to find a backup solution that'll run across multiple external drives, that can't all be mounted simultaneously.

My main server has a 6TB JBOD. As I've upgraded over the years I've kept the old drives and used them in USB enclosures as backup media, I've got about a dozen or so ranging in size from 1TB to a lowly 20GB. They're an even mix of IDE and SATA and I can have two online at any one time.
Previously I've used rsync to manually back up to these old drives, but I've pretty much outgrown this.
My backup needs are simple, I just need to take a snapshot of the data and local config settings every couple of months but I need to maximise the storage on the older drives, I need to use every byte I can.

I've had a look at Amanda but it seems too complex for my needs. I've read about the vtapes but when it started talking about calculations and rotation schedules I thought I was a bit out of my depth.
As another wrinkle to the situation, the 6TB filesystem on the server is 86% full which I reckon will be about 95% by the end of the year so I can't use any of it for backup purposes except whatever's needed for indexes or databases.
Can anyone help ?

---

### Post by gzarkadas on 2010-08-09
You can use dar. It is a command line backup program that can make backups of any size in slices (-s option), pause between them (-p option) or execute a user command (-E option). It also supports compression, encryption and many other features (the drawback is that the man page is huge; there is a lot to read). dar is the name of the package to install also (in the universe repo, if I remember well).

The only problem is that you have media with differing capacities, while the slice size cannot change dynamically, so you will need to make some planning ahead.

First calculate a slice size that will use the most space of all media used to backup. For example, if you have three disks #1, #2, #3 with capacities 250 GB, 320 GB and 1 TB, then two appropriate slice sizes are:

[LIST]
[*]20G (12 slices in #1 with 10 GB unused, 16 in #2, 51 in #3 with 4 GB unused)
[*] 50G (5 slices in #1, 6 in #2 with 20 GB unused, 20 in #3 with 24 GB unused)
[/LIST]
 
Then make a script with the following contents, to handle the drive-full condition. Store it in your /usr/local/bin (so that it will be in your path) and make it executable.

```

!/bin/bash

# $1: backup-path
# $2: size
# $3: size-as-int

while [ $(df -B ${2} ${1} | awk 'NR>1 {print $2}') -lt ${3} ]
do
    printf "Backup drive %s cannot hold another slice;\nmount a new drive and press enter to continue.\n" ${1}
        read
done 

```You are now ready to make the backup, using the following command line:

```

dar -s <size> -c <archive-path>/<archive-name-prefix> -R <path-to-backup> -E 'drive-check <archive-path> <size> <size-as-int>' 

```
[LIST]
[*]<size> is your selected slice size (say 20G)
[*] <archive-path> is the path to the backup disk (say /media/backup)
[*] <archive-name-prefix> is the name of your backup (dar will append slice number and the .dar extension to it)
[*] <size-as-int> is the selected slice size (in our example 20G) as a  pure number (in this case: 21474836480). You have to calculate it  beforehand
[/LIST]
 When the backup drive becomes full, the script will print its message and pause to wait your input. Then use another terminal to do the following actions in order:

[LIST]
[*]sync
[*]unmount the (old) backup drive
[*]physically replace the drive with the next
[*]mount the (new) backup drive at the same path
[*]verify the mount has been done
[/LIST]
Then switch back to the original terminal and press enter to continue.

Append option `-z9' or `-y9' to the above command line to use gzip or bzip2 compression at the maximum level (done within each slice).

If your drives' sizes are listed in SI units (multiples of 1000 instead of 1024) then make the calculation as before and insert the options `-aSI' in dar's command line and `--si' in df's command line (inside the script).

---

### Post by draxenato on 2010-08-09
That sounds exactly what I'm looking for, thanks very much for that :)

---

