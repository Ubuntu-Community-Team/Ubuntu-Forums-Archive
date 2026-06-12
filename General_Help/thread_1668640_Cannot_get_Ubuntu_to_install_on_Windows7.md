---
title: "Cannot get Ubuntu to install on Windows7"
date: 2011-01-16
forum: General Help
---

### Post by jessie312 on 2011-01-16
I am new to installing Ubuntu and cannot get it to install on my desktop windows7 and can't see any obvious reasons why it won't work.

The Ubuntu home page led me to believe that the wubu download would be the easiest way to download and install ubuntu side-by-side with my windows7, but I'm not finding that to be true.  Know I have now tried to download that windows ubuntu installer 3 times now and it fails every time.

I have complete admin rights to my desktop.  After over an hour of dowloading I keep getting message "Permission denied" and it refers me to the log file.

The last few lines of the log files states:

01-16 12:28 DEBUG  TaskList: ### Finished get_metalink
01-16 12:28 DEBUG  TaskList: New task download
01-16 12:28 DEBUG  TaskList: ### Running download...
01-16 12:28 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
01-16 13:28 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


01-16 13:28 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
01-16 13:28 DEBUG  TaskList: ### Finished download
01-16 13:28 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
01-16 13:28 DEBUG  TaskList: # Cancelling tasklist
01-16 13:28 DEBUG  TaskList: # Finished tasklist
01-16 13:28 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'

---

### Post by jonbonjovi on 2011-01-16
Try launch the installer as Administrator.

---

### Post by jonbonjovi on 2011-01-16
Try launch the installer as Administrator.

---

