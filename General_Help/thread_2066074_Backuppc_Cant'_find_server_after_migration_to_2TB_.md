---
title: "Backuppc: Cant' find server after migration to 2TB drive?"
date: 2012-10-03
forum: General Help
---

### Post by TechMansoor on 2012-10-03
In brief, I installed backuppc via:

sudo apt-get install backuppc

and after doing so I attempted to move the directory where backuppc will do backups to a 2TB drive better known as /dev/sdb or /media/Backups/backuppc

This is what I did as outlined by the following article:

> 
Set up a Symbolic Link from the Old Location to the New

Remove the old BackupPC data directory:

   sudo rm -r /var/lib/backuppc

And replace it with a symbolic link to the new data directory (note the order of the parameters is target path before link path):

   sudo ln -s /media/usb0/backuppc /var/lib/backuppc

Set the owner of the symbolic link to 'backuppc':

   sudo chown -h backuppc:backuppc /var/lib/backuppc

Check the symbolic link is present and has the right permissions:

   sudo ls -al /var/lib

And check that it links to the right contents:

   sudo ls -al /var/lib/backuppc

Restart the server (just to make sure everything reinitializes):

   sudo shutdown -r now


[http://tristram.squarespace.com/home/2012/3/11/moving-the-backuppc-data-directory-to-an-external-hard-disk.html]("http://tristram.squarespace.com/home/2012/3/11/moving-the-backuppc-data-directory-to-an-external-hard-disk.html")

After doing this as stated, I come back to backuppc and I get a:

Error: Unable to connect to BackupPC server via the web interface.

The command line, upon trying to restart backuppc, gives off this error:
> 
" * Restarting backuppc... 
No process in pidfile '/var/run/backuppc/BackupPC.pid' found running; none killed.
2012-10-08 16:24:51 Can't create a test hardlink between a file in /var/lib/backuppc/pc and /var/lib/backuppc/cpool.  Either these are different file systems, or this file system doesn't support hardlinks, or these directories don't exist, or there is a permissions problem, or the file system is out of inodes or full.  Use df, df -i, and ls -ld to check each of these possibilities. Quitting..."


I"m pretty sure it's due to the fact that something isn't mounted.

Can anyone guide me as to what needs to be done in order to make Backuppc come back online?

---

### Post by TechMansoor on 2012-10-05
anyone? I can't seem to crack whats going on?

---

