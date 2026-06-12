---
title: "give multiple users access to drives"
date: 2010-08-11
forum: General Help
---

### Post by prayersfor.rain on 2010-08-11
Hi all, sorry if this is a dumb question, but I can't figure it out.

I just created a 2nd user on my computer.  I've got the hard drive that ubuntu runs on, and then a 2tb drive for media.  If the 2tb is mounted on my desktop, it won't show up on his desktop even if I'm logged out.  It won't show up on his unless I unmount on mine.

If I'm logged out I'm obviously not using it.  So why doesn't it show up?
He has all privileges.
Is there a way to make this work without having to unmount?  

I'm running karmic btw.
If you need computer info let me know what to type into the terminal and whatnot and I'll paste it all here!
Thanks :)

---

### Post by bodhi.zazen on 2010-08-11
Is this a drive connected via USB ?

What are the permissions of the drive when mounted ?

My guess is you will need to add an entry in fstab and mount the device manually.

---

### Post by prayersfor.rain on 2010-08-11
No, it's not USB, it's plugged in like my other hard drive (same type of cords, I think sata?)

How do I find the permissions to my drive? Basically I click on it, it asks me for my password, and then it opens.  I can read/write.  When I'm able to get it on the other username, same story, and I can read/write.

I know nothing about fstab. :(

edit: I found [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131).  I'm gonna figure this out!

---

### Post by bodhi.zazen on 2010-08-11
Add an entry in fstab and you should be good to go.

See :  [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by prayersfor.rain on 2010-08-11
Ok according to Storage Device Manager (Pysdm), every drive I have is set to mount at boot time.  I changed ALL of them so that any user could mount/unmount the drives.  
Switched to other user, 2tb doesn't show up at all.  When I switch back it's on my mine. If I unmount and switch it'll show up in his and if he mounts it and we switch back to me, it doesn't show up for me.

---

