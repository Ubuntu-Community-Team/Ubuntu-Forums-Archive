---
title: "Can I remote access a machine running pen drive linux?"
date: 2010-01-22
forum: General Help
---

### Post by T3KN33K on 2010-01-22
More specifically, is there a built in function, or third party app that I can use to remotely access a machine, and to copy files from a broken Windows hard-drive partition (NTFS)?  

The scenario is, a relative's computer, who lives in a different town about 4 hours away, will not boot, from some catastrophic Windows error.  She has no CD to attempt repairing the installation, and has several GB's worth of pictures on the computer.

My plan was to make a thumb drive with a bootable installation of Ubuntu or some smaller distro, and give it to a friend who commutes regularly between the two cities, and have my relative boot via that drive, and back up all the pictures and what-nots before attempting a fresh installation.

She does have a ~500gb usb HDD to copy onto.

Possible?  Am I missing an easier solution?

---

### Post by T3KN33K on 2010-01-22
EDIT: blank post.

---

### Post by T3KN33K on 2010-01-24
Bump

---

### Post by jamesisin on 2010-01-24
You will want to enable ssh on the Linux build you are sending over on the drive.

You will also want to configure their router, if they have one, to pass ssh (port 22) to the machine in question (which will require either setting a static IP on that Linux build or changing the IP route on the router to whatever is dynamically assigned at boot--the former being easier probably).

Then they can boot and you can ssh into that machine.  From ssh you can use scp (secure copy) to copy the files back to your machine.  Depending upon connection speeds, this could take quite a while.  Alternatively, you could use cp (copy) to copy the files to some local (their locality) drive.

If you plan to copy the files to the thumb drive you are sending, you will want to set up a space (probably easiest to create a separate data partition) for storing those files.

At least, this is one possible route.  There may well be others.

---

### Post by T3KN33K on 2010-01-28
Thanks for your response, that's exactly what I was looking for.  

:p

---

### Post by jamesisin on 2010-01-28
Excellent.  Good luck with that.

If appropriate, please mark this thread as SOLVED in Thread Tools above.

---

### Post by t4thfavor on 2010-01-28
Install to a USB Drive install ssh, and set a password on the user account you can remember.

Have the relative boot the broken pc with both the 500GB, and the broken drive installed. Have them login, and find out their external IP by visiting [www.whatismyip.com](www.whatismyip.com) 

Walk them through forwarding port 22 to the inside pc if applicable.

Then you should be able to mount both drives, and copy all files over to the 500GB using rsync -auv /broken/drive/mount /media/500gb/drive

you should not try to download several GB of data over the internet it would take you forever.

---

