---
title: "USB LiveCD with persistent file - Boot problems...HELP!"
date: 2010-09-07
forum: General Help
---

### Post by JasonHippy on 2010-09-07
I've had a quick look through the forum and not seen anything pertaining to this particular problem, but basically I've got a LiveCD of Ubuntu 9.10 installed on a USB stick.
It has a persistent file for storing documents and things. And I've not set any users up on it, so it usually boots straight to the ubuntu desktop.

I've been using it since 9.10 came out without any problems, but I tried booting it this evening and it keeps bringing up the 9.10 login screen and I can't get to the desktop..

I've done a ctrl-alt F1 to bring up a terminal and it's got loads of error messages from the boot that look like this:
```
Use of uninitialised value $value in substitution (S///) at /usr/share/per15/Debconf/Format/822.pm line 65, <$__ANONIO__> line 574
```each line like this highlights a different error.

Then underneath that block of error messages are these few lines:
```
Using CD-ROM mount point /cdrom/
Identifying.. [a82748218497810ab752bc71b8f73056-2]
Scanning disc for index files..
```finally there are several lines which say:
```
Authentication failure
```Obviously something's gone a bit screwy. It was definitely shut down properly the last time it was used, so I'm just assuming that something went wrong during the last shutdown.

Anybody got any ideas what might be causing this? Or any ideas to fix it?

If not, is there any way I can mount the persistent virtual file-system to be able to retrieve any of my documents that were on there?? I'm assuming that the persistent file is the casper-rw file. 
I can plug the stick into my old tablet PC which runs 9.04, so if there is any way I can mount the file-system on the USB stick in 9.04 to retrieve my files, that would be very handy!

There are a few things that I've been working on that I really need to be able to retrieve. Ironically I was just booting the PC to back-up the files I had stored on there when this whole mess occurred! Doh!

Incidentally, the only reason I've been running off a USB stick is 'cause the original HD in my laptop died and I haven't had the money to replace it. So the install on the USB stick is kinda handy!

Anyway, any suggestions will be helpful.
Thanks in advance.
Jason.

---

### Post by JasonHippy on 2010-09-07
Aha, never mind! I've found the answer in this thread (after a bit of trawling!):

[http://ubuntuforums.org/archive/inde...t-1028564.html]("http://ubuntuforums.org/archive/index.php/t-1028564.html")

Looks like I should've used less keywords in my previous searches!!

Don't know why I didn't think of doing that to start with! Doh!

Anyway, problem solved!

---

