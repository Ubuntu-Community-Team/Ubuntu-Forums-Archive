---
title: "root filesystem leak"
date: 2010-06-22
forum: General Help
---

### Post by ethanay on 2010-06-22
that is how i can best describe it:  like a memory leak, but only with the root filesystem.  it is now perpetually out of free space.  i can find no culprit file or files anywhere.  something invisible is sucking my free root space dry.  I should have ~3.3gb free:

/ directory folder properties (everything but /home):
```
325,429 items, totalling 5.5 GB
(some contents unreadable)
```

compare with:
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.8G  8.3G   25M 100% /
udev                 1003M  300K 1002M   1% /dev
none                 1003M  860K 1002M   1% /dev/shm
none                 1003M  288K 1002M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
none                  8.8G  8.3G   25M 100% /var/lib/ureadahead/debugfs
/dev/sda5              98G   43G   50G  47% /home
```

for the record, the 25mb free is only because i did an "apt-get autoremove"

so now i am getting standard errors: unable to launch programs with root permission, such as
[http://ubuntuforums.org/showthread.php?t=821443](http://ubuntuforums.org/showthread.php?t=821443)
and regular warnings that my filesystem has run out of space.

the error seemed to appear when i tried to print from [www.noteflight.com](www.noteflight.com), which is a flash-based web app.  printing used to work fine (albeit with limited functionality, thank you Adobe...).  

however, now when i try to print, the behavior is similar to this:
[https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/288570](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/288570)

except it happens at 300dpi...and it happens to a pdf printer or a physical printer.  other programs (word processor, text editor, etc) print fine to pdf or physical printer.  see attached cups error log.

i thought maybe it was a bug in flash, but another similar Ubuntu laptop behaves as expected...any clues?

---

### Post by arrange on 2010-06-22
You may try looking for any bulky files/folders, f.e.```

sudo du -ak --exclude=/home/* / 2> /dev/null | sort -n | tail -30
```

For comparison, on my system *tail -10* looks like this```

250716	/usr/lib/openoffice/basis3.2
251772	/usr/lib/openoffice
709236	/usr/share
808124	/var/cache/apt/archives
835872	/var/cache/apt
845112	/var/cache
917756	/usr/lib
1022020	/var
1828128	/usr
3140512	/
```(sizes are in KiB)

---

### Post by dcstar on 2010-06-22
> **ethanay said:**
> that is how i can best describe it:  like a memory leak, but only with the root filesystem.  it is now perpetually out of free space.  i can find no culprit file or files anywhere.  something invisible is sucking my free root space dry.  I should have ~3.3gb free:
.........

```
gksudo baobab
```

If your check the many other posts already on this sort of issue, you will find that log files may be filling up.

---

### Post by bhuvi on 2010-06-22
if u downloaded and installed a lot of programs then download cache might be filling up,type:

sudo apt-get clean

to clear download cache

and try to open disk usage analyser in root mode and see which folder is using more space.

---

### Post by philefluxx on 2010-06-22
> **dcstar said:**
> 

If your check the many other posts already on this sort of issue, you will find that log files may be filling up.


Yup, had this same problem. What is funny is the log was from rinted which I was playing with. While I was working with rinted I wasnt getting anything written to the log file. I actually uninstalled it because it wasn't working the way I hoped and logging seemed kinda weak. 12 hours went by and I came back to my box to find my harddrive was 100% full. When performing df -h I could see the ureadahead directory seemed like it was housing all my space which obviously it wasn't. Stupid left over log files running away....:confused:

---

### Post by ethanay on 2010-06-22
Thank you all for your suggestions.  Similar symptoms does not equal the same problem.  This is unique from a log file issue -- I had already checked that, which is why I posted.  I appreciate that dcstar is trying to cut down on useless reposting clutter, but sometimes there are good reasons for new posts :)

Based on arrange's suggestion, we have the culprit:

```
$ sudo du -ak --exclude=/home/* / 2> /dev/null | sort -n | tail -30 
[...snip uninteresting results...]
516048	/usr/src
538812	/var/spool/cups/d00508-001
673688	/var/spool/cups/d00511-001
916244	/var/spool/cups/d00500-001
916248	/var/spool/cups/d00513-001
916272	/var/spool/cups/d00514-001
1363088	/usr/lib
1536560	/usr/share
3671836	/usr
3962352	/var/spool/cups
3962540	/var/spool
4380176	/var
8498640	/
```

Five files totaling *3.8Gb* from failed print jobs initiated from [www.noteflight.com](www.noteflight.com) (flash-based web app).  I couldn't see them because doing so requires root permissions.  The files get larger and larger without ever printing, and tie up printing resources (CUPS) so that no web browser can use them.  

Since printing seems to work outside of the flash context, does it not implicate flash specifically vs CUPS?

What are the next steps?  File a bug or try to resolve?

I had already tried reinstalling Flash, CUPS and Ghostscript packages, to no avail.  I'm holding off on the 10.04 install because I'm in the middle of a project, and don't want to interrupt my workflow until I'm done (or at least at a stopping point).

---

### Post by ethanay on 2010-06-27
> i thought maybe it was a bug in flash, but another similar Ubuntu laptop behaves as expected...any clues?

> Since printing seems to work outside of the flash context, does it not implicate flash specifically vs CUPS?

What are the next steps? File a bug or try to resolve?

i was wrong.  it appears to be a CUPS bug.  now all three computers are experiencing the same behavior, making printing from Noteflight impossible.  i don't think it's either Noteflight or Flash -- they've been constant on the computers.  it seems to be behavior introduced since a couple of the latest CUPS updates.

i thought it might be similar to:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/275691](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/275691)
but the appearance of that bug predates this issue.

new bug filed:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/598940](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/598940)

---

