---
title: "rysnc not preserving modified date"
date: 2009-08-27
forum: General Help
---

### Post by dpatel on 2009-08-27
Hi -

I use rsync to backup my files to my network hard drive. I mount the shared folder on my network hard drive using cifs (have used smbfs too). The network drive is formatted as NTFS to allow sharing with Windows too.

The issue I have is I can't seem to get it to preserve modified date. It always sets modified date to the backup date. For example, if on my laptop the mod date=22 Apr 09, when backed up this will change to today's date and will NOT be 22 Apr 09.

I've tried option -t within rsync but it doesn't work.

Any ideas??

---

### Post by XCan on 2009-08-27
Could you paste the command you're using? If it absolutely does not work, it may be something to do with NTFS. I've never run it on NTFS so I dunno, but for testing purposes, have you tried the same command but pointing to one of your current Ubuntu dirs, just to check if it's an incorrect syntax error.

---

### Post by dpatel on 2009-08-28
I haven't got the command with me but it was something like:

rsync -n -v -t --ignore-existing --delete /sourcedir -e ssh /dest

Forgot to mention I ssh to my network drive in case that is relevant.

I guess I can try to one of my ext3 folders. But if that works correctly I still don't what to do about backing up to my NTFS drive. :confused:

---

### Post by Copernicus1234 on 2009-08-28
Which arguments are used in /etc/fstab to mount the ntfs partion?

---

### Post by dpatel on 2009-08-28
I mount the drive using smbfs or cifs. If I remember correctly I only use -t option. Maybe -o.

I've put all this into a script to backup my data. So it mounts the drive, does backup and unmounts.

---

### Post by Copernicus1234 on 2009-08-28
I was just thinking there may be a flag for mounting that enables file modification time to be preserved. Might be worth checking into.

When using cp, you can use cp -p to preserve it. Try to copy a file to the ntfs partion that way and see if it keeps the modification time.

---

