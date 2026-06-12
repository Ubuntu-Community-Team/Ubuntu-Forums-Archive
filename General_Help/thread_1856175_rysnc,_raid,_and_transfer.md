---
title: "rysnc, raid, and transfer"
date: 2011-10-07
forum: General Help
---

### Post by mithril knight on 2011-10-07
I have a large raid 5 array that has around 2.5tb of 5gb files. I transfered them using rsync:
rsync -vz /src/ -e ssh user@ip:/dest/
I was getting around 6 MB/s. Using the command:
dd if=/dev/zero of=/dev/sdb-vol/test bs=4k count=[FONT=Verdana]195126
I get 269MB/s. This is over a gigabit switch(with gigabit network adapters). There is no network, just switch and two computers. How can I make this faster?
Is this the correct command to use when syncing? It seems like it isn't doing delta transfers(even though it says it does), because when I run the command again, it is slated to take as long as it would the first time. This isn't ok, because this server will be moved offsite once I have it all set up. I need to know how to use rsync (or something) to transfer 2.5tb+ of files. This directory will be synced between multiple computers over the WAN and the transfers will need to be two way between all of them(achieved by switching source and destination of rsync command)
The array is fully built and running
[/FONT]

---

### Post by oldfred on 2011-10-08
Your z parameter uses compression which is for slow connections. 

This is what I use but this is just hard drive to hard drive.

#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

#rsync -auvP /home /media/backup
#rsync -auvP /share /media/backup
#rsync -auvP /media/floppy /media/backup
#rsync -auvP /etc /media/backup
echo "done"
exit 0

---

