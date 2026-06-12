---
title: "HELP! 9.10 no longer booting"
date: 2010-01-04
forum: General Help
---

### Post by tamccullough on 2010-01-04
I updated yesterday.
I'm not sure if problems started before or after.

The problem yesterday[http://ubuntuforums.org/showthread.php?t=1371888](http://ubuntuforums.org/showthread.php?t=1371888)

Went to bed last night and left the computer running, something weird occured this morning (media file wouldn't play) so I just decided to restart.

now I am getting this,

Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.

ctrl-d just brings me back to the above error message.

in the GNU GRUB version window
I no longer have 
Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
listed

using the other two listed 16 and 14 does nothing

HELP! I have work to do! :'(

---

### Post by pedro_orange on 2010-01-04
I imagine you've edited your /etc/fstab and done something wrong.

If I were you, I'd revert to a backup of that file and reboot. Or edit it to be what it was before you started messing around with it.
Always make a copy of any configuration file you edit before you do so!

---

### Post by tamccullough on 2010-01-04
I only added the one line at the end of the fstab to always mount the 2nd hd. Is there a way to edit the fstab in the maintenance shell?
I've tried but don't have the priviliges.

---

### Post by pedro_orange on 2010-01-04
Become root.

> su

Then it will ask you for the root password.

---

### Post by LMP900 on 2010-01-04
I had a similar issue several weeks ago. I searched the forums on my Kindle (luckily, I still had an internet device available!) and found a workaround. This post isn't quite the post I found when I had my issue, but it's exactly what I did:

[http://newyork.ubuntuforums.org/showpost.php?p=7249469&postcount=2](http://newyork.ubuntuforums.org/showpost.php?p=7249469&postcount=2)

---

### Post by tamccullough on 2010-01-04
Thanks guys.

Doesn't seem to be helping.
Although I have to admit I can't seem to figure out how to use the command su

It looks like the maintenance terminal already has me logged in as root

I've tried 
sudo nano /etc/ftsab
but it won't let me save over the file because it is read-only

---

### Post by tamccullough on 2010-01-04
In case this helps - I am using the 64-bit desktop version of 9.10.

Thanks

---

### Post by tamccullough on 2010-01-04
Thanks for those that responded.

I decided to re-install ubuntu

I'll try not to do whatever I did to make it funk out in the future.

Cheers

---

