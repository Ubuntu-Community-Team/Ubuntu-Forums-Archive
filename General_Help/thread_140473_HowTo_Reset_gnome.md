---
title: "HowTo Reset gnome"
date: 2006-03-06
forum: General Help
---

### Post by tarpon_bill on 2006-03-06
Hello,

Been messing with the gnome panel settings and want to reset gnome to factory initial conditions. Can I just delete the .gnome* directories or is there an easier way?

Thanks in advance.

---

### Post by knalle on 2006-03-06
you should be able to reset your gnome from system settings, deleting **~/.gnome** will also kill many app settings

---

### Post by tarpon_bill on 2006-03-06
Well I accidentally screwed up the menu system and it's not usable. So much for customizing. There doesn't appear to be anything in the .gnome directory.

If I delete the .gnome directory -- is all I lose the settings?

---

### Post by ComplexNumber on 2006-03-06
**tarpon_bill**
if you really mean factiory settings, then if you delete your account (need to be root to do this), create a temp account(ie because if there is only only one user, you will not be able to log in at all because logging in as root isn't allowed on ubuntu), then manually delete your home directory, then create new user, everything will be 'as new'.

---

### Post by knalle on 2006-03-06
yes, from a system point of view its all ok to delete the .gnome dir and reset your X11.

i use KDE and killed my .kde folder once i messed it up, and i found that many kde apps stores it settings in the .kde folder instead of their own damn folder. very annoying

---

### Post by tarpon_bill on 2006-03-06
Yeah, I have other users ... but was looking for a less drastic way than deleteing the whole account.

Next time I will play menus with a temp account :rolleyes:

---

### Post by tarpon_bill on 2006-03-06
OK, got gnome back to the original state, just deleted all the .gnome* directories and the .gconf* directories.

Thanks ...

---

### Post by ComplexNumber on 2006-03-06
> .gconf*
thats where most of your personal settings are stored for your account.

---

