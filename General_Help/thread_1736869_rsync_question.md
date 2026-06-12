---
title: "rsync question"
date: 2011-04-22
forum: General Help
---

### Post by krumpy on 2011-04-22
I'm doing my first backup with rsync and it's behaving different than i expected.  Here's my cmd:

rsync -r -t -v --progress -s /home/matt /media/netdrive/UbuntuBackup

It looks like it's looking at files outside the UbuntuBackup directory (destination).  Like in the sample output below:

matt/.gvfs/public on 192.168.1.100/Matt Profile/AppData/Local/Temp/StructuredQuery.log 54 100%    0.10kB/s    0:00:00 (xfer#15102, to-check=1313/1777

"192.168.1.100/Matt Profile/AppData/Local/Temp/StructuredQuery.log" is up a level in the directory tree from UbuntuBackup.

I guess I'm confused why it's looking at anything outside the destination directory?

---

### Post by oldfred on 2011-04-22
Do you have a symlink in /home that links to that. I found my rsync started following all my links in /home which I did not want. I just wanted all of /home and then back up the symlinked data folders separtely.

I copied this from another post so I knew what the parameters were.
#!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks

# ! not 
if [ ! -d /mnt/Backup ]; then
     mkdir /mnt/Backup
fi
 
mount -t ext3 /dev/sda2 /mnt/Backup

echo "starting..."
# So I know additional sources
cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/sources.list.backup
# List of all installed applications
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/ubuntu-files
# System Boot Configuration
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh

#rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

rsync -aurvlP /home /mnt/Backup
#rsync -auvP /share /mnt/Backup
#rsync -auvP /media/floppy /mnt/Backup
#rsync -auvP /etc /mnt/Backup
echo "done"
exit 0

If you have a symlink add -l 
See man rsync for more info.

---

### Post by krumpy on 2011-04-27
Thanks.  Works great.  I'm still having some trouble with rsync, but I'll post that to a different thread.

---

