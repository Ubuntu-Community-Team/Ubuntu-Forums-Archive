---
title: "usb ntfs hard disk mount as user with fstab"
date: 2010-01-23
forum: General Help
---

### Post by Gatemaze on 2010-01-23
Hello,

I have a usb hard disk formatted as ntfs... When mounted it is mounted as root:root /media/<label> 777. Reading and writing is no problem as any user can change them... but there is a problem when deleting a file as it forbids creating a trash bin and hence files are permanently deleted... I've been trying playing with fstab with the following line

UUID=<uuid> /media/DATA ntfs-3g defaults,locale=en_GB.UTF-8,id=<user_id>,gid=<group_id>,umask=007 0 0

but with no luck as the volume is not mounted... The error message is 'You are not privileged to mount the volume XX'. Btw, /media/DATA is already created with ownership to the user and the group given in the fstab file.

Any clues?

Many thanks

---

### Post by quixote on 2010-01-25
I've had the same problem and would like to know the solution!  The workaround I used was to add "user" to the options in the fstab line.  Then it's owned by whichever user mounted it and Trash works.  But if you want or need root ownership, that's obviously not a useful workaround.

---

### Post by Gatemaze on 2010-01-25
> **quixote said:**
> I've had the same problem and would like to know the solution!  The workaround I used was to add "user" to the options in the fstab line.  Then it's owned by whichever user mounted it and Trash works.  

This ("user") would work with vfat partitions but not with ntfs ones using ntfs-3g ([http://www.tuxera.com/community/ntfs-3g-faq/#useroption2](http://www.tuxera.com/community/ntfs-3g-faq/#useroption2))... The workaround is actually documented in the ntfs-3g faq ([http://www.tuxera.com/community/ntfs-3g-faq/#useroption](http://www.tuxera.com/community/ntfs-3g-faq/#useroption))... There is no real problem with my fstab line above...

> **quixote said:**
> 
But if you want or need root ownership, that's obviously not a useful workaround.


I am confused... Why would you want root ownership on a disk mounted by user??

---

### Post by quixote on 2010-01-25
*Why would you want root ownership on a disk mounted by user?*

I meant that if the partition should be owned by root, but accessible to user for some stuff, then user can't use Trash.  I realize that normally that makes sense.  But once I was trying some backup software which wanted everything owned by root, so if I tried to deal with my own photo directories after a restore, I'd have to first chmod everything.  The solution, of course, was to switch to rsync ;).

Thanks for the ntfs links.  Those are the answers I was looking for.

---

