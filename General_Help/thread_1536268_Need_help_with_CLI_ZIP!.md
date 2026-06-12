---
title: "Need help with CLI ZIP!"
date: 2010-07-21
forum: General Help
---

### Post by AKD1 on 2010-07-21
I'm trying to create backup/archive my Ubuntu 10.04 system files (so I can restore it in case my system get corrupted). More specifically, I'm trying to zip the important files in my root directory not including my home directory (which includes my documents which I backup separately/more frequently) to an external hard drive attached via USB (called 'My Book').

Since File Roller didn't give me quite the level of control I was looking for, I created a script that I could execute to backup and archive regularly. Here's a snippet:
 [INDENT]cd /media/"My Book"/"Linux Backups"
NOW=$(date +"%b-%d-%y")
LOGFILE=Backup_DellLatitudeD620_Ubuntu_FileSystem-$NOW.log
[/INDENT]#
# To create zip file (non-sequential archive) use following command: ([http://linux.about.com/od/commands/l/blcmdl1_zip.htm](http://linux.about.com/od/commands/l/blcmdl1_zip.htm))
#     Example: zip -r TestZip ~/Documents/AKD/Mom -x ~/Documents/AKD/Mom/'Mom insurance'\*
#    Note: to exclude directories enter the flag -x PATHNAME1\* PATHNAME2\* 
[INDENT]sudo zip -r -T -v Backup_Root_FileSystem-$NOW / -x /media/'My Book'\* /media\* /proc\* /sys\* /mnt\* /dev\* /cdrom\* /home\* /'lost+found'\* | tee -a $LOGFILE

echo "Checking validity/accuracy of zip file" | tee -a $LOGFILE
unzip -tq Backup_DellLatitudeD620_Ubuntu_FileSystem-$NOW.zip | tee -a $LOGFILE
[/INDENT]When I execute this, only the log file is created and no zip file is created. The terminal window shows that it starts to add files, but from the excluded directories, starting with "My Book". 

Here is the output from the terminal window:[INDENT]    zip warning: name not matched: /media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/.ecryptfs/amit/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWaYzpV4BZNwE-Qh48zmJMclYKU5FCiPjGrmOaTTyDAaI9Fntyc9NqKorE--/ECRYPTFS_FNEK_ENCRYPTED.FWaYzpV4BZNwE-Qh48zmJMclYKU5FCiPjGrmyhIsd61dTNeTv55Pf0BKdU--/ECRYPTFS_FNEK_ENCRYPTED.FXaYzpV4BZNwE-Qh48zmJMclYKU5FCiPjGrmzvWat6NI8.-y6RjyyN2B4oY-BjxoZQEpY3FjgechqqM-
..    zip warning: name not matched: /media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/amit/.wine/dosdevices/z:/media/My Book/.Trash-1000/files/Backup 2/home/.ecryptfs/amit/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWaYzpV4BZNwE-Qh48zmJMclYKU5FCiPjGrmvAsAMnV1l-zVIrsM5pdJc---/ECRYPTFS_FNEK_ENCRYPTED.FYaYzpV4BZNwE-Qh48zmJMclYKU5FCiPjGrmS3RWzEDzFaf5QQQCBcFq8QigXiN.bw05hgK1C5JmGZrChgJVSOOVIACsXA9j5cx7
..
zip error: Out of memory (local_to_display_string)
[/INDENT]Can someone tell me what I am doing wrong? Why can't I seem to create a zip file that excludes all files/directories from external drives including /media/*? If I read correctly, isn't the following the correct zip command syntax? If so, why does my output indicate directories from the excluded path being added (/media/My Book/.Trash-1000/*)?

zip -r FILENAME DIRECTORY_TO_ZIP -x PATH_TO_EXLUDE\*

Btw, I'm a newbie to Linux, so if this is basic, please excuse me.

---

### Post by quixote on 2010-07-23
I don't know anything about how to use zip, but I can tell you what I've done for this.

1) use [Clonezilla Live]("http://clonezilla.org/") to back up your whole system partition and don't worry about excluding files. It's fast and allows compression.  (However, I just recently had to try to use it to restore a system partition and it didn't work for me!  So I'm not sure what to say.  It seems to work for everyone else.)

2) Use rsync.  You have as much control over what to exclude as you want.  I don't use it with compression, but I'm sure it's one of its many options. You won't get a complete backup of a system if it's the one you currently are booted into.  You need to boot with a liveCD or USB to backup your regular system partition.  Typing "man rsync" (without quotes) in a terminal will give more info than you want.  However, just for example, after booting from a livecd, let's say you've mounted your regular system partition at /mnt/rootpart and your usb drive for backup at /mnt/usb. (If you need more detail on that step, just let us know.)

```
sudo rsync -avu --delete --exclude "*Trash*/" --exclude "/home/"  --exclude="*~" /mnt/rootpart/ /mnt/usb 1>/home/your-user-name/log-backup.txt 2>/home/your-user-name/log-backup-errs.txt
```Explanation: you need to use sudo since many system files can only be read by root.  -avu: a:archival, preserve permissions & times, v: verbose, u:update mode, --delete: which means delete files on the backup which have been deleted in the original. You may not want the latter option, especially if you want to preserve backups of different versions of the same file.  (Usually more of a concern with data files.)  You can have as many excludes as you want, or none.  Those are just examples. "/mnt/rootpart/" is the source and it's important to have the final /.  "/mnt/usb" is the target where the backup will go, and it's important *not* to have a final slash.  Otherwise the backup will go in a subdirectory: /mnt/usb/rootpart.  You can omit the 1> and 2> things if you want.  They redirect the output that would normally scroll up the screen to files in your home directory.

Hope that's some use. :D

---

### Post by AKD1 on 2010-07-23
Thanks quixote, I'll try out the rsync command. 

But does anyone know why the zip command isn't working with the -x flag? I think I'm using it according to how it's outlined in the man pages.

---

