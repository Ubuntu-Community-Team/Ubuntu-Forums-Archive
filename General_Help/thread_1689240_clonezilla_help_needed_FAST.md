---
title: "clonezilla help needed FAST"
date: 2011-02-16
forum: General Help
---

### Post by boelle1 on 2011-02-16
i have read my butt in 1000 bits and still have the same problem as the poster in this thread: [http://ubuntuforums.org/showthread.php?t=403971](http://ubuntuforums.org/showthread.php?t=403971)
 
i have posted this on clonezilla forum, might be that it could tell a bit more. I need a fix fast as i'm without pc ;)
 
"i have read my butt in 1000 bits to figure this one but no luck. I did manage to make the backup with no problems, but today i need to do a restore but i was left with a partion of unknown format and not able to boot my xp laptop. the partion was formated in fat32 and even tried to make a clean partion in fat 32 still the same showstopper. i can quite remember what compression i used but it was the slowest of them all to make the image dir as small as possible and also to make an restore as fast as possible. for some reason clonezilla thinks i made an backup of sdb but my laptop only holds one drive so gparted and other utils says its sda... however i can see that clonezilla handles this by making some temp files so i can retstore to sda what could be wrong here? the lappy is now dead... lucky me all my docs are on sda2 and my system should go on sda1 so its not a total loss.... i'm on my girlfrineds pc so i'm not in total darkness, also i have the image files/dir on a usb stick initial i asked clonezilla to store the image on sda2 but after backup i moved them to my usb stick as not to loose them, clonezilla can read them right.... "

---

### Post by quixote on 2011-02-17
I'm not sure from your description what you have.  You cloned all of sda?  Only sda1?  Only sda2?  You have a working back up of sda2?  

Could you make a list that shows it a bit more?  Something like this:

laptop
   was: sda1 (system, format ext4-ntfs-or-??), sda2 (data-or-whatever?, format: ??))

all of sda backed up as drive-to-drive (?), or partitions backed up to image files?  or what?

tried to use drive-to-drive to restore?  image file to sda?  image file to sda1?

etc, etc.

I'm pretty sure all your stuff is okay and that once the details are right, it'll restore just fine.  But until the details are clear, it's hard to know what to suggest.

---

