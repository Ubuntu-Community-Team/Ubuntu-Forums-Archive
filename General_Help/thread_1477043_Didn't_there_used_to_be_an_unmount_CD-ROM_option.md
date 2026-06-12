---
title: "Didn't there used to be an unmount CD-ROM option?"
date: 2010-05-08
forum: General Help
---

### Post by imbjr on 2010-05-08
When I pop a DVD into the burner drive, the system mounts it, but I need to unmount it so that xfburn can have at it.

However, right-clicking the CD-ROM drive symbol shows no unmount option. I may be mistaken, but I thought there was an option to do an unmount for CD-ROMs in Karmic - but it seems to have gone in Lucid.

I had to drop to the terminal to do it.

---

### Post by dino99 on 2010-05-08
with nautilus or any file browser, select the device and right click on it to unmount, or with cli: sudo umount /dev/???, or install mountmanager then tweak it as you need

---

### Post by imbjr on 2010-05-09
> **dino99 said:**
> with nautilus or any file browser, select the device and right click on it to unmount, or with cli: sudo umount /dev/???, or install mountmanager then tweak it as you need

Mmm, so do it with nautilus for a GUI approach. Odd, I did think the desktop icon would have had the option.

---

### Post by imbjr on 2010-05-29
> **imbjr said:**
> Mmm, so do it with nautilus for a GUI approach. Odd, I did think the desktop icon would have had the option.

Just got around to noticing that nautilus does not in fact have an unmount option. It has a load of CD-ROM options including eject - but I need to unmount before using xfburn.

I started using xfburn after all the trouble the other burners cost me.

---

### Post by CharlesA on 2010-05-29
Yup, it only has "eject" which unmounts the drive and ejects the cd.

It would probably be easier to unmount it using the terminal.

---

### Post by imbjr on 2010-05-29
> **CharlesA said:**
> Yup, it only has "eject" which unmounts the drive and ejects the cd.

It would probably be easier to unmount it using the terminal.

But like I said I could have sworn there used to be a right-click unmount option.

---

### Post by CharlesA on 2010-05-29
> **imbjr said:**
> But like I said I could have sworn there used to be a right-click unmount option.

Karmic had it, yes. I don't know if you can add it to Lucid or not.

There is something called nautilus-actions in the repos, but I don't know if it will do what you want.

---

### Post by imbjr on 2010-05-30
> **CharlesA said:**
> Karmic had it, yes. I don't know if you can add it to Lucid or not.

There is something called nautilus-actions in the repos, but I don't know if it will do what you want.

Yeah, I found that and considered adding it, but I'm happy enought with dropping to the terminal. 

I guess they thought that with all the other CD-ROM options now available, they didn't want to keep yet another, but one that helps burning.

---

