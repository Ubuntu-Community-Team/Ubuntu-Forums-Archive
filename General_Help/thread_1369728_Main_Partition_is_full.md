---
title: "Main Partition is full?"
date: 2010-01-01
forum: General Help
---

### Post by CRIMPS on 2010-01-01
So, I have two hard disks (120GB + 200GB) that are formatted in ext3 and are set up in one main partition (total of 283GB I believe).  My problem is that the partition shows as full.  I started looking at what I have on this system and I show 21GB of data total.  This breaks down to about 16GB in my Home Directory and another 3GB in the Usr Directory.  I copied the Home Directory data to a different computer so my pics, music, docs, etc. are safe.  

One of the disks is suspect, but I was thinking this wouldn't affect both drives the partition is spanned across.  I could definitely be wrong on that.

I ran Disk Usage Analyzer and I scanned the File System.  This also shows 21GB of usage.  I started to create a backup using the Simple Backup Config utility.  The problem is this is creating a huge backup file... in fact, the backup is failing because I don't have enough disk space.

So, how do I figure out what is causing this Partition to fill up?

Im thinking my only option is to reformat my new Hard Disk I just bought, reload/setup Ubuntu, then copy my data to this new drive.  I guess I was looking for a way to back up my user data and simply restore.  Since I can't create a backup I guess this isn't an option.

Does anyone have any ideas how I can troubleshoot this before I start from scratch?

Thanks!

---

### Post by tom4everitt on 2010-01-01
Well, you generally don't need a fancy backup utility for that. Just drag and drop the folders you want to keep to your backup hard drive. 

Then you can just reformat your hard drives, and copy the folders back.

I don't know what the problem might be, but not creating one big partition on two different hard drives will probably avoid it.

---

### Post by rnerwein on 2010-01-01
hi - as first i'm a little confused about your disk space - you wrote you get a 120gb and a 200gb disk and you belive the sum is 283 :-)??? . 
ok - the first is -> open a terminal, switch to root-id, cd / , # du -k . ( remember the last line - the sum of used disk space) then #df -k is there a huge diffence about the du -k . and the df -k command then please post a output of the df -k and du -k . (only the sum of the du -k . command) and then i will you post back my idea of a hidden file - this is a little bit longer to explain. 
--> real programmers don't use mice <---

---

### Post by oldfred on 2010-01-01
I agree with merwein on checking totals:

I also like to houseclean occasionly:
HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean
Sometimes this does more?
sudo apt-get dist-upgrade#

 empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

