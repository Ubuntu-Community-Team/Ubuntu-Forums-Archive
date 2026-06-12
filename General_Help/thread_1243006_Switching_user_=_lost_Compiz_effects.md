---
title: "Switching user = lost Compiz effects"
date: 2009-08-17
forum: General Help
---

### Post by UranUtan on 2009-08-17
Hi,

Using Ubuntu 9.04 x32. Video card is ATI 9200. Compiz is working OK with Visual Effects = normal. Nothing fancy, I just need transparency effects and also because Avant Windows Navigator requires Compiz. Other than that 99% of Compiz effects are not used.

I have created a new user (let's call it user2) who doesn't have the privilege of doing admin task. When I login under user2, the Visual effects is always none and cannot be set to normal. If I reboot the computer and log in as user2 then I can set Visual Effects from None to normal. But unfortunately, when switching to user1, then Compiz is gone and Ubuntu refuses to to turned it on.

[COLOR="Red"]Question:[/COLOR] Can compiz effects be activated for more than 1 user on the same computer?

Thanks in advance for any help.

---

### Post by owise1 on 2009-08-18
I have a similar problem - had compiz setup OK and all running as expected.  Added new user and now unable to get compiz to run for either user.  Not sure if adding user was the problem or an update.

---

### Post by owise1 on 2009-08-19
as usual I found the answer in the forum.  I had used a second monitor and the virtual resolution was larger than the video card could support with compiz.  Reset xorg.conf and restarted X and all well.

Still blown away that this little underpowered eeepc can deliver such impressive graphics

---

### Post by UranUtan on 2009-08-20
I can't believe this bug still exists in version 9.04. I have only one monitor. Everybody uses the same resolution. Only one user can have Compiz active. I have reset xorg.conf by
```
sudo dpkg-reconfigure xserver-xorg
```
But the problem remains the same. Could it be an intentional design of Compiz that only ONE user can have Visual Effects set to Normal?

EDIT:
Just failed to reproduce the issue on another machine using Ubuntu 9.04 x64 with another video card nVidea GeForce 9300. The 2nd user could have Visual Effects set to Normal (instead of None). So I assume the cause of the troubles I have with the previous machine is either:

1- a bad upgrade from 8.10 to 9.04
or
2- ATI video driver issue (model = ATI Radeon Mobility 9200)

---

