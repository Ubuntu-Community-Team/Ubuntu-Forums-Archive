---
title: "Backup help!"
date: 2010-12-04
forum: General Help
---

### Post by obis666 on 2010-12-04
Hi, I would first like to apologize if this info exists somewhere else, I just could not find what I am looking for due to the massive amounts of info available and my lack of knowledge regarding technical terminology with backups.

Here is what I am trying to do. I have 2 media servers running ubuntu, 1 with ubuntu 10.10 and 1 running 8.04, each machine has 2 1tb external hard drives connected (totaling 4tb, 2tb of the 4tb contains unique data). I have an exact copy of all data on the 2 1tb hard drives, on both of the 2nd drives connected. I have been doing all my backups manually and it has become too consuming.  My problem is I cannot find backup software that just copies and deletes the data exactly from the primary to the secondary drives without adding a bunch of other directories or .rar-ing the contents, or doing some kind of weird incremental magic... All I need is an exact replica of drive 1 on drive 2. 

For example if I use backintime I copy external drive 1 to external drive 2, I get snapshots 

drive 1
/media/drive1/

drive 2
/media/drive2/backintime/new_snapshot/backup/media/drive1/

Each backup creates a snapshot, which is useful for backing up my home directory, but I make a lot of changes and will be making backups daily. 

Any help would be amazing and save me so much time, thanks in advance.

---

### Post by obis666 on 2010-12-05
Looks like rsync might be what I am looking for, but I can't seem to find anyone doing anything similar to what I am doing.

---

### Post by drdos2006 on 2010-12-05
This is my bash file run from terminal to load the shared folders on my desktop named : mounterservershares.sh
###--------------------------------------------
# !/bin/bash
# Must install server and client NFS programs first

sudo mkdir /media/sdb1-shared
sudo mkdir /media/sdc1-shared
# IP address of server is fixed at 192.168.0.25

sudo mount 192.168.0.25:/media/sdb1/sdb1-shared  /media/sdb1-shared
sudo mount 192.168.0.25:/media/sdc1/sdc1-shared  /media/sdc1-shared
###
This is my bash file to update the server data from my desktop named : update-server.sh
 "man rsync" is your friend.
###----------------------------------------------
    #!/bin/bash


rm 		/home/unit/Documents/backup-log-sdb1.txt
bash 		/home/unit/Documents/MountServerShares.sh

## sdb1 is 1000 GB Hitachi SATA  ext3
rsync --verbose --recursive  --archive --modify-window=1 --times --update --delete-after  --progress --itemize-changes --log-file=backup-log-sdb1.txt   /media/sda1/Install/*   /media/sdb1-shared/Install/  
   
## sdc1 is 1000 GB Hitachi SATA  ext3
 
rsync  --verbose --recursive  --archive --modify-window=1 --times --update --delete-after  --progress --itemize-changes --log-file=backup-log-sdc1.txt  /media/sda1/Install/*   	/media/sdc1-shared/Install/
 
	 umount    /media/sdb1-shared/ 
	 umount    /media/sdc1-shared/ 
####

---

