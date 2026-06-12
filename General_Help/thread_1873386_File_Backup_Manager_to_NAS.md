---
title: "File Backup Manager to NAS"
date: 2011-11-01
forum: General Help
---

### Post by JoeFriday49 on 2011-11-01
[FONT=verdana]I was looking for a file backup manager that will make a mirror image of my "home" folder on an NAS drive...  It appears that [/FONT]Pybackpack  0.5.8 will do the job, but so far I have been unable to make it copy to  my network drive.  It will create the directories I specify, but won't  copy the files...  Anyone have any experience with this program?

Currently running 10.04LTS and have no problem reading and writing files to this drive manually.

---

### Post by JoeFriday49 on 2011-11-01
As an afterthought here are the contents of the logfile that gets written to the NAS drive.  If it's telling me it doesn't have permissions then I can't understand that because it puts this file on the network drive I'm trying to back up to...

<snip>
Tue Nov  1 12:53:42 2011  Making directory /home/joefriday49/.gvfs/volume_1 on 192.168.10.110/rdiff-backup-data/increments
Tue Nov  1 12:53:42 2011  Reading globbing filelist /home/joefriday49/.pybackpack/sets/test/filelist
Tue Nov  1 12:53:42 2011  Starting mirror / to /home/joefriday49/.gvfs/volume_1 on 192.168.10.110
Tue Nov  1 12:53:42 2011  Processing changed file .
Tue Nov  1 12:53:42 2011  Processing changed file .systemfile
Tue Nov  1 12:53:42 2011  Regular copying ('.systemfile',) to /home/joefriday49/.gvfs/volume_1 on 192.168.10.110/rdiff-backup.tmp.1
Tue Nov  1 12:53:42 2011  Exception '[Errno 13] Permission denied: '/home/joefriday49/.gvfs/volume_1 on 192.168.10.110/.systemfile'' raised of class '<type 'exceptions.OSError'>':
  File "/usr/lib/pymodules/python2.6/rdiff_backup/robust.py", line 32, in check_common_error
    try: return function(*args)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/FilenameMapping.py", line 162, in listdir
    return map(unquote, self.conn.os.listdir(self.path))

Tue Nov  1 12:53:42 2011  ListError .systemfile [Errno 13] Permission denied: '/home/joefriday49/.gvfs/volume_1 on 192.168.10.110/.systemfile'
Tue Nov  1 12:53:42 2011  Processing changed file Joe Friday
Tue Nov  1 12:53:42 2011  Removing directory /home/joefriday49/.gvfs/volume_1 on 192.168.10.110/.systemfile

---

### Post by JoeFriday49 on 2011-11-29
> **JoeFriday49 said:**
> As an afterthought here are the contents of the logfile that gets written to the NAS drive.  If it's telling me it doesn't have permissions then I can't understand that because it puts this file on the network drive I'm trying to back up to...

<snip>
Tue Nov  1 12:53:42 2011  Making directory /home/joefriday49/.gvfs/volume_1 on 192.168.10.110/rdiff-backup-data/increments
Tue Nov  1 12:53:42 2011  Reading globbing filelist /home/joefriday49/.pybackpack/sets/test/filelist
Tue Nov  1 12:53:42 2011  Starting mirror / to /home/joefriday49/.gvfs/volume_1 on 192.168.10.110
Tue Nov  1 12:53:42 2011  Processing changed file .
Tue Nov  1 12:53:42 2011  Processing changed file .systemfile
Tue Nov  1 12:53:42 2011  Regular copying ('.systemfile',) to /home/joefriday49/.gvfs/volume_1 on 192.168.10.110/rdiff-backup.tmp.1
Tue Nov  1 12:53:42 2011  Exception '[Errno 13] Permission denied: '/home/joefriday49/.gvfs/volume_1 on 192.168.10.110/.systemfile'' raised of class '<type 'exceptions.OSError'>':
  File "/usr/lib/pymodules/python2.6/rdiff_backup/robust.py", line 32, in check_common_error
    try: return function(*args)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/FilenameMapping.py", line 162, in listdir
    return map(unquote, self.conn.os.listdir(self.path))

Tue Nov  1 12:53:42 2011  ListError .systemfile [Errno 13] Permission denied: '/home/joefriday49/.gvfs/volume_1 on 192.168.10.110/.systemfile'
Tue Nov  1 12:53:42 2011  Processing changed file Joe Friday
Tue Nov  1 12:53:42 2011  Removing directory /home/joefriday49/.gvfs/volume_1 on 192.168.10.110/.systemfile
Still not having any luck with this one...

---

