---
title: "/mnt ignored by GNOME Panel"
date: 2009-08-09
forum: General Help
---

### Post by Elep.Repu on 2009-08-09
I edited fstab to automount a drive to /mnt, but the Gnome panel ignores the drive's existence.

Can I fix this? Is there a better panel out there?

---

### Post by ridgeland on 2009-08-09
What line did you put in /etc/fstab?
Did you reboot after the change to /etc/fstab?
What does it mean the gnome panel ignores it?
Does df see it?

---

### Post by Elep.Repu on 2009-08-10
> **ridgeland said:**
> What line did you put in /etc/fstab?
Did you reboot after the change to /etc/fstab?
What does it mean the gnome panel ignores it?
Does df see it?

What I'm saying is that, the GNOME panel ignores mounted volumes in /mnt.
The option to mount the drive will be there in the Places panel, but when mounted to /mnt manually it disappears: is what I'm saying.

Yes, I had restarted after editing fstab. (I know how to edit it.)

Is it possible to change what GNOME indexes, drive-wise? If so, that would apply to this.

---

### Post by mcduck on 2009-08-10
Volumes mounted outside of /media are not supposed to show on desktop, Places-menu or the panel applet.

If you want the drive to show in these places, mount it inside /media, if not, mount in anywhere else.

---

### Post by ridgeland on 2009-08-10
Yes.  I mount all my partitions under /mnt like /mnt/sda5, /mnt/sda6 ...
I don't use /media because I don't want them on my desktop and showing up in File->Open lists.  You can use gconf-editor to control if they display or not (if mounted on /media) see apps->nautilus->preferences etc.  
I'm used to calling the panel just the narrow 28 pixel stripe at the top or bottom so I was slow to follow your question.

---

