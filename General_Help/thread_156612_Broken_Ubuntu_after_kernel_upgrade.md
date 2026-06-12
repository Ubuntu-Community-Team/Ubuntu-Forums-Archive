---
title: "Broken Ubuntu after kernel upgrade?"
date: 2006-04-07
forum: General Help
---

### Post by Internight on 2006-04-07
Hello,
I don't exactly recall what I was upgrading but kernel was upgraded for sure. From default 2.6.12-9-386 to 2.6.12-10-386. So I have no sound working(only in gdm screen), sudo do not work either(can't use sudo program, sudo -s -H etc... - asks for password and does nothing). Tried booting old kernel - same thing.
So maybe someone could advice something.

---

### Post by nanotube on 2006-04-07
check your /etc/group file, see if your user is still in the "admin" group,  the "audio" group, and in the "adm" group.
the adm/admin should allow you to use sudo, and being in the audio group allows you to use the sound device.

if your user is not listed for those groups, reboot to single user mode (reboot and choose recovery mode, it will dump you into root console), and edit the file.

if your /etc/group is correct, and it still does not work, then we will have to troubleshoot some more. :)

---

### Post by Internight on 2006-04-07
Thank You. That helped :)

---

### Post by nanotube on 2006-04-07
great. :) 
i wonder which upgrade it was that screwed with your /etc/group, though... that "shouldn't" happen.

---

