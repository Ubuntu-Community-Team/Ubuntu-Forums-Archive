---
title: "Disk appears to be read only after PC crash"
date: 2012-05-18
forum: General Help
---

### Post by nikhil_1203 on 2012-05-18
Hi,

I have a few concerns. My laptop just recovered from a crash recently. I ran the disk scan to check for errors and errors were reported and fixed as well, but ever since, I have been observing a few problems.

1) Whenever I try to download something using Mozilla Firefox, I get an error message:
/tmp could not be saved, because an unknown error occurred.
Try saving to a different location.

2) I did try playing around a wee bit. When I try to do sudo -i, I get a message that says: sudo: Can't open /var/lib/sudo/nikhil/0: Read-only file system.

When I do df -l to check if the disks are full, I get the message:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             98429572   8433268  84996368  10% /
udev                   1472880         4   1472876   1% /dev
tmpfs                   591960      1012    590948   1% /run
none                      5120         0      5120   0% /run/lock
none                   1479892       276   1479616   1% /run/shm
/dev/sda7            100959656  22462904  73368256  24% /home
/dev/sr0               4458080   4458080         0 100% /media/Backup Disc- 8


3) When I try to install anything using the ubuntu software center, I first get a message: 
Failed to download package files
Check your internet connection.

When I close the dialog box, I get another message: 
An unhandled error occured.
There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 215, in _process_transaction
    self.commit_packages(trans, *trans.packages)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 282, in commit_packages
    self._apply_changes(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 923, in _apply_changes
    with self._frozen_status():
  File "/usr/lib/python2.7/contextlib.py", line 17, in __enter__
    return self.gen.next()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 951, in _frozen_status
    frozen_dir = tempfile.mkdtemp(prefix="aptdaemon-frozen-status")
  File "/usr/lib/python2.7/tempfile.py", line 310, in mkdtemp
    dir = gettempdir()
  File "/usr/lib/python2.7/tempfile.py", line 254, in gettempdir
    tempdir = _get_default_tempdir()
  File "/usr/lib/python2.7/tempfile.py", line 201, in _get_default_tempdir
    ("No usable temporary directory found in %s" % dirlist))
IOError: [Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/']

Please guide me to get rid of this.

Thanking you in anticipation,
Nikhil

---

