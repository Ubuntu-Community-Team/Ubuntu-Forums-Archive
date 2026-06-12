---
title: "K3b problems..."
date: 2006-03-23
forum: General Help
---

### Post by dartmusic on 2006-03-23
There was an update in the repos a few days ago for K3b.  I blindly just updated and now I'm having issues with DVD+RWs.  Whenever I try to write to one I get an error saying something about "not able to umount."  So, before I burn any DVD+RWs I have to remember to unmount the disk and then burn.  

So, my questions are thus:  does anyone know how to fix this?  And secondly, (I'm at work or I'd just look for myself) are there multiple versions of K3b in the repos?  Can I simply uninstall the newest version and reinstall an older version, one that didn't have this problem?

Thanks!

---

### Post by dragonfyre13 on 2006-03-23
There is no version control in the repos. Sorry. I know that there are a few programs that have it in my debian archive, like wine, but that is because of the major differences in use.

As for resolving the problem, post a bug report on the K3B site. I know that you can install an older version after uninstalling the newer one, so if you do a search for K3B debs, you could very well find it.

First, though, I would check to make sure that you are both running K3b With root permissions, (sudo) and that it is looking for the drive in the right place. This sounds more like a configuration issue than a software issue. I know mine works fine, and I update every time there is a new version out.

---

### Post by Barrakketh on 2006-03-23
Are you using the K3B from Breezy Backports?

---

### Post by dartmusic on 2006-03-23
From the Breezy Backports...yeah, I should know the answer to that.  I'm going to say "yes" as I know I have those repos active.

As for the config...I'll check it when I get home, but why would it change?  Everything was functioning correctly (in fact, perfectly) in K3b (which was a huge problem for me in SuSE) until about 3 days ago when this started happening.  I didn't change any configs, so I don't know why that would be the issue, but I'll check when I get home.  Any tips of what to look for?

Thanks...

---

### Post by Barrakketh on 2006-03-23
What is the version you have installed?  I have 0.12.14 in Dapper and need to look through the changelog to see if that's a known bug.

---

### Post by dartmusic on 2006-03-23
Again, not at home right now so I can't answer for certain, but I DO believe that I am using 12.14.

I simply let apt update it when it was available, so I can't understand why settings would have changed.  And, considering it worked correctly "out of the box" from the original install and through a couple of subsequent updates, I can't understand why anything would have changed with regard to settings/configs/etc.

---

### Post by Barrakketh on 2006-03-23
Does the error look like this:

> Executing 'builtin_dd if=/tmp/kde-w2/k3b_image.img of=/dev/hde obs=32k seek=0' 
umount: alleen root kan /dev/dvdrecorder ontkoppelen van /media/dvdrecorder 
:-( /dev/hde: unable to proceed with recording: unable to unmount 

Some of that looks like it might be dutch or something, but the general error might be recognizable.

---

### Post by dartmusic on 2006-03-23
Yep, that's the error!  Any idea how to remedy without manually unmounting before burning every time?

---

### Post by Barrakketh on 2006-03-23
Can you try burning the DVD by launching k3b with "kdesu k3b"?

---

### Post by dartmusic on 2006-03-23
Alright...check this out: I came home tonight and had a few different things to try as per inquiries on this here site.  The first thing I did was to (attempt to) disable the xcompmgr stuff detailed by poofyhairguy for cool desktop goodies.  I tried to comment out the two lines in xorg.conf that were mostly responsible and of course xorg.conf couldn't load when I tried restarting the X server.  I copied over an older version of the file and when I restarted the X server, I was using the nv driver instead of the proper nvidia driver.  I left it alone, just to see what was going to happen.  I decided to try adding a newly downloaded TV show to a DVD+RW.  I checked the settings and everything looked in order so just for the hell of it, I tried burning without unmounting and guess what...it worked just fine.  So, either it's the xcompmgr or the nvidia driver causing this problem, or so it would seem.

Does this sound like crazy-talk to anyone?

---

### Post by dragonfyre13 on 2006-03-27
A bit, but I've heard wierder. Perhaps it just needed a service restarted, or the drives remounted. At the risk of sounding like a windows guy, perhaps it needed a restart.

I had that problem a while ago, I just remembered. I restarted the computer (fresh off the windows wagon) and it worked again. Of course, I was also playing around with mounting the CD drive, and when I restarted, it reinitialized Fstab, but still.

---

### Post by dartmusic on 2006-03-27
Ha...yeah, tried restarted, tried everything I can think of.  And now, the problem is back.  Whenever I try to write on a non-blank DVD+RW I have to manually unmount it before I hit burn.  

Grumble...oh well.

---

### Post by asta on 2006-03-28
Turn off automount?

---

### Post by dartmusic on 2006-03-28
What happens if I do turn off automount?  I'm assuming that my external devices then won't mount, which would be even more of a problem.

I'm just curious why I seem to be the only person having this problem.  It's not the end of the world, but I'd like to know what to do as it might help with other things in the future.

Oh well...thanks for looking.

---

