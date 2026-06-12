---
title: "Possible Permisions Issue"
date: 2011-09-23
forum: General Help
---

### Post by Thelasko on 2011-09-23
Sorry folks, but this is a long story.:(

It all started because I'm having issues with ureadahead filling up my root partition.  My root partition only had ~20MB of free space left and my system was running very slow.  I shutdown the system and booted to the live CD where I ran fsck to fix the issue per [this thread.]("http://www.linuxquestions.org/questions/linux-server-73/ubuntu-server-incorrectly-claiming-disk-full-and-persistent-ureadahead-debugfs-791114/")  It worked once before, but the problem reoccurred.

While I ran fsck on my root partition, I figured it might be a good idea to run it on my /home partition as well.  It's just checking the filesystem for errors, right?

Now I think I'm having issues with permissions on my system.  The first being when I opened Thunderbird and received an error: > Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disk space to copy the mailbox

While attempting to resolve this issue, I tried to open synaptic and received the message: > Failed to run usr/sbin/synaptic as user root
Unable to copy the user's Xauthorization file.

I can open synaptic by typing *sudo synaptic* just fine, it just won't start through GNOME.

Any ideas on how I can fix these issues?  I'm running a fully updated and patched version of Ubuntu 10.04.3 LTS Lucid Lynx 64-bit.

---

### Post by ajgreeny on 2011-09-23
In a terminal can you please run ```
ls -ahl /home/$USER
```and report back the output which will tell us what permissions are set at the moment.

---

### Post by Thelasko on 2011-09-23
A lot of blank space and:
```
-rwxr-----  1 lasko lasko 5.6K 2010-09-26 12:07 testpage.py
drwxr-xr-x  2 lasko lasko 4.0K 2010-06-17 06:45 .themes
drwx------  5 lasko lasko 4.0K 2010-06-13 19:36 .thumbnails
drwx------  3 lasko lasko 4.0K 2010-06-12 22:04 .thunderbird
-rwxr-----  1 lasko lasko 3.3K 2010-09-26 12:07 timedate.py
-rwxr-----  1 lasko lasko 8.0K 2010-09-26 12:07 toolbox.py
-rw-rw-rw-  1 lasko lasko 823K 2008-06-18 06:02 translog.20070611183944.log
drwx------  2 lasko lasko 4.0K 2010-08-22 19:59 .tsclient
drwxrwxr-x  2 lasko lasko 4.0K 2010-06-21 21:14 Ubuntu One
drwxr-----  2 lasko lasko 4.0K 2010-09-26 12:12 ui
drwxr-----  2 lasko lasko 4.0K 2010-09-26 12:12 ui4
-rwxr-----  1 lasko lasko  24K 2010-09-26 12:07 unload.py
-rw-r-----  1 lasko lasko   29 2010-09-26 12:09 unreleased.inc
drwx------  2 lasko lasko 4.0K 2010-06-30 07:01 .update-notifier
drwxr-xr-x  3 lasko lasko 4.0K 2011-04-06 18:51 Videos
-rw-------  1 lasko lasko  676 2011-03-22 19:33 .viminfo
-rw-r--r--  1 lasko lasko   56 2010-11-13 16:04 vlc-log.txt
-rw-rw-rw-  1 lasko lasko   62 2008-06-18 06:01 wifi card settings
-rwxr-----  1 lasko lasko 2.5K 2010-09-26 12:07 wificonfig.py
-rw-rw-rw-  1 lasko lasko 467K 2009-10-21 16:40 WinFriendsAnd_InfluencePeople.pdf
drwx------  2 lasko lasko 4.0K 2009-01-07 18:44 wireshark
drwxr-xr-x  2 lasko lasko 4.0K 2011-01-13 20:20 Work
drwx------  6 lasko lasko 4.0K 2008-09-09 22:40 workingelfs
drwx------  4 lasko lasko 4.0K 2008-09-23 18:45 workspace
-rw-r--r--  1 lasko lasko  559 2010-06-13 19:36 .xscreensaver-getimage.cache
-rw-------  1 lasko lasko 4.5K 2011-09-23 17:55 .xsession-errors
-rw-------  1 lasko lasko 3.5K 2011-09-21 18:41 .xsession-errors.old

```

---

### Post by ajgreeny on 2011-09-24
That all looks normal, but there seems to be a lot missing, and what do you mean by "A lot of blank space"?

Where are all your data folders such as Documents, Downloads, Desktop, Music, etc etc, or did you just show the bottom part of the much longer output?

---

### Post by Thelasko on 2011-09-25
There was a longer output but it was all blank.  Just hundreds of empty lines.  Only those last few lines contained any text.

---

