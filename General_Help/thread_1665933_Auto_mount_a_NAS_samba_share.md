---
title: "Auto mount a NAS samba share"
date: 2011-01-13
forum: General Help
---

### Post by niblettes on 2011-01-13
I'm pretty new to Linux.  But with Maverick I'm going to try to kick the Windows habit for good.  

One problem I'm having is with getting some apps to access NAS hosted files and folder over samba.  Two examples are photo managment apps and backup apps, which seem to only want to work with local files and folders.

I have come across a number of articles about cifs, autofs, gigolo, fstub, etc (including the autofs community documentation).  But so far I've had no luck in auto mounting a samba shared resource as local.

Can anyone point me to a definitive tutorial, or provide an explanation on how I might accomplish auto mounting samba shares?

---

### Post by niblettes on 2011-01-14
Bump

---

### Post by dread22 on 2011-01-14
Have you tried mounting the folder?

> sudo mount -t cifs -o user=USERNAME,workgroup=WORKGROUP,password=PASSWORD //192.168.1.1/smb /localmntfolder

Modifying the above command should give you access to the samba folder. You may also want to add it to your /etc/fstab for auto-mounting.

---

### Post by niblettes on 2011-01-15
Yes I can get mount the samba share with no problem with either nautilus or the command prompt -- but I want it to *auto* mount. 

Furthermore I need Linux to see the mounted resource as local so that certain apps  (like Back in Time which can only access local resources) can access the resource.

I also like the feature of autofs that closes unused connections after a time out to avoid chewing up bandwidth -- fstab doesn't do this.

I'm surprised this seems so difficult because it strikes me as something many Linux users would need.

---

### Post by niblettes on 2011-01-17
Anyone?

---

### Post by niblettes on 2011-01-20
Well I guess this question has stumped the Ubuntu community.

There are a few people who would like to kick the Windows habit completely.  

Unfortunately it seems that its still unrealistic for mainstream users with home networks to switch to Linux because basic resource sharing that's trivial in Windows XP (an OS over a decade old) is either impossible in Linux or a big secret that no one will share.  

Either way, I'm disappointed that I'll have to keep Windows for a bit longer and Ubuntu will have to remain on my old desktop as a curiosity rather than a real Windows replacement.

---

### Post by niblettes on 2011-01-20
deleted repeat

---

### Post by niblettes on 2011-01-20
deleted repeat

---

