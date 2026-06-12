---
title: "catch 22 on lost password"
date: 2009-12-25
forum: General Help
---

### Post by pwcogpsy on 2009-12-25
I've read the posts on resetting a lost password for Ubuntu, but we have a Dell netbook with the delay preset to zero on displaying the grub menu.  So, I can't get into the menu.

I tried to edit menu.1st to change the delay, but can't because it wants the password.

Very frustrated! Help!

---

### Post by chewearn on 2009-12-25
You would have to find a way to boot from an external device, like a USB flash drive (not sure if you have a bootable liveUSB of some linux distro lying around) or USB CD-ROM (with a Live CD inserted).

---

### Post by coffeecat on 2009-12-25
> **pwcogpsy said:**
> I tried to edit menu.1st to change the delay, but can't because it wants the password.

You can edit menu.lst (that's an L, not a one) if you boot up a live session from a bootable USB stick. If you mount your root partition and use gedit with administrative privileges (open it with 'gksudo gedit /path/to/menu.lst') you'll be able to edit it. The password in a live session is blank, so there's no problem in sudo-ing.

For another way, but you still need a bootable USB stick with Ubuntu on it, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1163371](http://ubuntuforums.org/showthread.php?t=1163371)

I'm afraid I was less than useful to the OP in that because I had not yet heard that Dell could do something as bizarre as set the menu.lst delay to zero. But look at aysiu's posts #7 and #12. That sounds like the way to go.

---

### Post by garyed on 2009-12-25
Try hitting the "Esc" key at bootup.
I had a similar problem & I just kept hitting the "Esc" key & the Grub menu came back up.
If you're using Grub2 (9.10) the try the Shift key instead.
Good luck

---

### Post by coffeecat on 2009-12-25
> **garyed said:**
> Try hitting the "Esc" key at bootup.

Um - check the OP. Dell sets the grub delay to zero so you can't get into the menu. Esc doesn't work.

---

### Post by Barriehie on 2009-12-25
I used to have issues with remembering passwords but not if they're on the bottom of the coffee mug... :)

Barrie

---

### Post by pwcogpsy on 2009-12-26
Thanks for the constructive help.  I'll try booting from a flash drive.

---

