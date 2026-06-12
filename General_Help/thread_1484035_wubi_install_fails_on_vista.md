---
title: "wubi install fails on vista"
date: 2010-05-15
forum: General Help
---

### Post by hyperyoda on 2010-05-15
Argh all that downloading for nothing, it fails when it is around 98% finished with install! Giving a permission denied error, yet that makes no sense because I am running as Administrator account in Windows Vista Home Premium (64-bit on amd64).

BTW I followed the recommended fix on the WubiGuide and it doesn't work.

It says to copy the ISO file (ubuntu-10.04-desktop-amd64.iso) into the same directory as the wubi.exe installer file. I did that and it still goes through the whole long process of downloading the ISO file and gives the same error at the end :(

[https://wiki.ubuntu.com/WubiGuide?action=fullsearch&context=180&value=permission+denied&titlesearch=Titles#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?](https://wiki.ubuntu.com/WubiGuide?action=fullsearch&context=180&value=permission+denied&titlesearch=Titles#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?)

Here is the relevant tail of the log file. 

05-15 07:04 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-15 07:04 INFO   saplog: Checking block bindings..
05-15 07:04 INFO   saplog: Key verified successfully.
05-15 07:04 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

05-15 07:04 DEBUG  TaskList: ### Finished get_metalink
05-15 07:04 DEBUG  TaskList: New task download
05-15 07:04 DEBUG  TaskList: ### Running download...
05-15 07:04 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
05-15 08:04 ERROR  TaskList: Traceback (most recent call last):
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


05-15 08:04 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-15 08:04 DEBUG  TaskList: ### Finished download
05-15 08:04 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-15 08:04 DEBUG  TaskList: # Cancelling tasklist
05-15 08:04 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-15 08:04 DEBUG  TaskList: # Finished tasklist

---

### Post by dandnsmith on 2010-05-15
I'd say your trouble started before any permissions errors were indicated.
It looks as if you're trying the install with the download wrapped up inside the install, and you'd be better off looking for a download which passes the md5sum check before you start on the wubi install - that way, should you get a permissions error, you can sort out the error without having to re-download.

Just a thought

---

### Post by hyperyoda on 2010-05-15
> **dandnsmith said:**
> I'd say your trouble started before any permissions errors were indicated.
It looks as if you're trying the install with the download wrapped up inside the install, and you'd be better off looking for a download which passes the md5sum check before you start on the wubi install - that way, should you get a permissions error, you can sort out the error without having to re-download.

Just a thought

Thanks will try that.

---

