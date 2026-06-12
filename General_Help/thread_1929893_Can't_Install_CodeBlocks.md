---
title: "Can't Install Code::Blocks"
date: 2012-02-22
forum: General Help
---

### Post by Gr1m3y on 2012-02-22
I got my hands on this Compaq Presario F700 to start learning Linux on. I loaded it up with 11.10 and it has been working like a charm for the most part. I have also been using it to code on, so I went to install Code::Blocks today and am getting an error that says I can't install new software through the software centre. I tried a few things I have found but am a little bit hesitant as the error isn't exactly the same and I know that you can screw things up if you are new to terminal. Here is the message I get:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

```

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the wesnoth-1.8-data package. This might mean you need to manually fix this package.

```Thanks for all the help! I appreciate it!

---

### Post by MG&amp;TL on 2012-02-22
> **Gr1m3y said:**
> ...screw things up if you are new to terminal...
Not...especially. :) No more than the GUI, anyway.

Can you post the output of:

```
sudo apt-get install codeblocks
```
Thanks.

---

### Post by Gr1m3y on 2012-02-22
I am running it now. It seems to be working fine, although it claims it will take a little under an hour. I also tried to install Gnash SWF Player for Firefox but got the same message. I will tell you how Codeblocks goes. Thanks for your help.

Edit: It dropped to 15 minutes! :)

---

### Post by Gr1m3y on 2012-02-22
Alright. This is what I got. It seems to have worked...

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  codeblocks-common libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
  wesnoth-1.8-data
Suggested packages:
  libwxgtk2.8-dev wx-common codeblocks-contrib libgnomeprintui2.2-0
  wesnoth-1.8-music
The following NEW packages will be installed:
  codeblocks codeblocks-common libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
The following packages will be upgraded:
  wesnoth-1.8-data
1 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 92.2 MB of archives.
After this operation, 153 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe wesnoth-1.8-data all 1:1.8.6-1 [82.7 MB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe libwxbase2.8-0 amd64 2.8.11.0-0ubuntu10 [581 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe libwxgtk2.8-0 amd64 2.8.11.0-0ubuntu10 [3,324 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe libcodeblocks0 amd64 10.05-2 [1,706 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe codeblocks-common all 10.05-2 [2,287 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe codeblocks amd64 10.05-2 [1,646 kB]
Fetched 92.2 MB in 7min 52s (195 kB/s)                                         
(Reading database ... 
dpkg: warning: files list file for package `wesnoth-1.8-data' missing, assuming package has no files currently installed.
(Reading database ... 159386 files and directories currently installed.)
Preparing to replace wesnoth-1.8-data 1:1.8.6-1 (using .../wesnoth-1.8-data_1%3a1.8.6-1_all.deb) ...
Unpacking replacement wesnoth-1.8-data ...
Selecting previously deselected package libwxbase2.8-0.
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.11.0-0ubuntu10_amd64.deb) ...
Selecting previously deselected package libwxgtk2.8-0.
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.11.0-0ubuntu10_amd64.deb) ...
Selecting previously deselected package libcodeblocks0.
Unpacking libcodeblocks0 (from .../libcodeblocks0_10.05-2_amd64.deb) ...
Selecting previously deselected package codeblocks-common.
Unpacking codeblocks-common (from .../codeblocks-common_10.05-2_all.deb) ...
Selecting previously deselected package codeblocks.
Unpacking codeblocks (from .../codeblocks_10.05-2_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up wesnoth-1.8-data (1:1.8.6-1) ...
Setting up libwxbase2.8-0 (2.8.11.0-0ubuntu10) ...
Setting up libwxgtk2.8-0 (2.8.11.0-0ubuntu10) ...
Setting up libcodeblocks0 (10.05-2) ...
Setting up codeblocks-common (10.05-2) ...
Setting up codeblocks (10.05-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by MG&amp;TL on 2012-02-23
Well....you don't seem to have a problem, so....if you still want to use software-center, and it's not working, try purging it and installing it again:

```
sudo apt-get remove --purge software-center
sudo apt-get install software-center
```

---

### Post by Gr1m3y on 2012-02-23
Well, I have no idea what was missing, but when the manual install was finished for Codeblocks, everything seemed to start working. The downside is that I have another issue now though, but it is unrelated. I will have to look into it a little more. Thanks a lot! I appreciate the help!

---

