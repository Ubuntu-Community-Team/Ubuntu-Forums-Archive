---
title: "rdiff-backup Out Of Space Error"
date: 2011-12-24
forum: General Help
---

### Post by jake.anq on 2011-12-24
Hi

I have being trying to set up a backup on an external hard drive using rdiff-backup, as the Gnome backup utility seems to be crashing the computer.
When I run the program, I get this:

```
Exception '[Errno 28] No space left on device' raised of class '<type 'exceptions.IOError'>':
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 280, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 346, in Backup
    backup.Mirror(rpin, rpout)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 38, in Mirror
    DestS.patch(dest_rpath, source_diffiter)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 232, in patch
    ITR(diff.index, diff)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/rorpiter.py", line 281, in __call__
    last_branch.fast_process(*args)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 529, in fast_process
    if self.patch_to_temp(mirror_rp, diff_rorp, tf):
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 559, in patch_to_temp
    rpath.copy_attribs(diff_rorp, new)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/rpath.py", line 181, in copy_attribs
    if Globals.eas_write: rpout.write_ea(rpin.get_ea())
  File "/usr/lib/pymodules/python2.7/rdiff_backup/rpath.py", line 1347, in write_ea
    ea.write_to_rp(self)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/eas_acls.py", line 114, in write_to_rp
    rp.conn.xattr.setxattr(rp.path, name, value, 0, rp.issym())

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 30, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 280, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/pymodules/python2.7/rdiff_backup/Main.py", line 346, in Backup
    backup.Mirror(rpin, rpout)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 38, in Mirror
    DestS.patch(dest_rpath, source_diffiter)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 232, in patch
    ITR(diff.index, diff)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/rorpiter.py", line 281, in __call__
    last_branch.fast_process(*args)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 529, in fast_process
    if self.patch_to_temp(mirror_rp, diff_rorp, tf):
  File "/usr/lib/pymodules/python2.7/rdiff_backup/backup.py", line 559, in patch_to_temp
    rpath.copy_attribs(diff_rorp, new)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/rpath.py", line 181, in copy_attribs
    if Globals.eas_write: rpout.write_ea(rpin.get_ea())
  File "/usr/lib/pymodules/python2.7/rdiff_backup/rpath.py", line 1347, in write_ea
    ea.write_to_rp(self)
  File "/usr/lib/pymodules/python2.7/rdiff_backup/eas_acls.py", line 114, in write_to_rp
    rp.conn.xattr.setxattr(rp.path, name, value, 0, rp.issym())
IOError: [Errno 28] No space left on device
```

This is the initial backup, so space for diffs should not be a problem and the destination has 1TB of space, 821gb of which is empty.  I am invoking rdiff-backup with:
```
rdiff-backup -v5 --exclude /mnt --exclude /media --exclude /proc --exclude /tmp --exclude /media --exclude /sys --exclude /dev --exclude /media/2879e147-0d87-4a7c-b836-62a96ca28728/ / /media/2879e147-0d87-4a7c-b836-62a96ca28728/
```

Using Ubuntu 11.10 with Gnome 3.

I would welcome any solutions or alternative methods for backup.

Thanks

---

### Post by Paddy Landau on 2011-12-24
Have you checked that your source data is significantly less than 1Tb?

Also, I notice you seem to be backing up your entire system. Is that what you want, or do you want to back up your home folders?

Rather than manually exclude /proc, /sys, /media and so forth, rather just use the following options:
```
--exclude-device-files
--exclude-fifos
--exclude-other-filesystems
--exclude-sockets
```Also exclude /tmp and /home/*/.cache (remember to put that within quotes).

I see you are backing up to the root folder of your media. Sometimes there are permissions problems with that. Therefore, create a new folder in your target media -- say, [FONT=Courier New][SIZE=2]/jake-backup[/SIZE][/FONT] -- and back up to there.

So your final line would look something like this (to make it easier to read, I've used the backslash to run it over several lines):
```
sudo rdiff-backup --verbosity 5 --exclude /tmp --exclude '/home/*/.cache'                  \
   --exclude-device-files --exclude-fifos --exclude-other-filesystems --exclude-sockets    \
   / /media/2879e147-0d87-4a7c-b836-62a96ca28728/jake-backup/
```Remember that each time you run rdiff-backup, it attempts to recover from its last crash; so, I'd recommend that you empty the target folder first!

Give that a try and see what happens.

**EDIT:** Oh, yes, as you are backing up your entire system, you need to use sudo.

---

### Post by jake.anq on 2011-12-25
Thanks, that seems to have completely fixed the problem.

---

