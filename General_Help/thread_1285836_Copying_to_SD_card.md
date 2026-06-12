---
title: "Copying to SD card"
date: 2009-10-08
forum: General Help
---

### Post by Robbyx on 2009-10-08
I have formated an SD card in a card reader and find that I can not mount the volume because I do not have the privileges. In nautilus it reports the permissions could not be determined. Mount manager does not seem to be able to make any difference as the owner and group is not changing in the properties of the drive. The owner is Root and neither group nor other users have write permission.

I can copy to it as SU, but not as my ordinary user name. 

What should I do to alter the permissions?

---

### Post by wojox on 2009-10-08
You can copy it as su or sudo?

---

### Post by Slim Odds on 2009-10-08
> **Robbyx said:**
> I can copy to it as SU, but not as my ordinary user name. 

What should I do to alter the permissions?

Change the permissions at the mount point

---

### Post by Carl Hamlin on 2009-10-08
> **Slim Odds said:**
> Change the permissions at the mount point

My experience has been that this works, but you have to re-mount after changing the permissions in order to get to your data.

---

### Post by Robbyx on 2009-10-08
I have it working by changing the settings for the drive in fstab. Thanks for the help in pointing me in that direction.

---

