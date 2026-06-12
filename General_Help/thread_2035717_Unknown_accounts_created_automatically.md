---
title: "Unknown accounts created automatically"
date: 2012-07-31
forum: General Help
---

### Post by Ben Neville on 2012-07-31
Hey Guys,

I would like to start off by saying I've been using Ubuntu 10.04 LTS at work for 2 years and loved every second of it.

I've started using 11.04 (upgraded to 11.10) at home and love it! (Been using for 4-5 months now)

However I have a few issues I've been unable to workout despite my research and forum hunting.

Firstly, I have had a bunch of user accounts appear on my system for no reason (Screenshot Attached). It's causing installing applications to report as 'Unable to Install' however they end up installing anyway
Where did they come from and are they ok to delete?

Secondly, I have a problem with my Creative Audigy 4 Sound Card
The sound crackles. I've tried the Installing Pulse Audio Software
Removing Power Save lines from alsa-base.conf
Installing Alsa mixer

What happens for example, when playing a youtube video. It' barely crackles. Then when I make it full screen, the sound is very jittery and crackles.

Any help would be greatly appreciated as I'm stuck

Regards
- Ben

---

### Post by dino99 on 2012-07-31
[https://help.ubuntu.com/8.04/serverguide/user-management.html](https://help.ubuntu.com/8.04/serverguide/user-management.html)

[http://www.ubuntugeek.com/how-to-createdisable-and-delete-new-user-account-in-ubuntu-11-10-oneiric-ocelot.html](http://www.ubuntugeek.com/how-to-createdisable-and-delete-new-user-account-in-ubuntu-11-10-oneiric-ocelot.html)

[http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html)

[https://help.ubuntu.com/community/SoundTroubleshooting/](https://help.ubuntu.com/community/SoundTroubleshooting/)

:guitar:

---

### Post by Ben Neville on 2012-07-31
I didn't add these accounts and I'm the only one that uses this PC
Where did they come from?
What could have created them?

---

### Post by techvish81 on 2012-07-31
there could be a broken install, if you don't want to further research and try, you can simply backup your imp stuff and clean install whatever version of ubuntu you like.

an upgrade gone wrong sometimes messes everything,.

i would recommend you to try the latest Ubuntu 12.04 as it is LTS. you will have 5 full years of support.

---

### Post by qamelian on 2012-07-31
It looks like you've installed the qmail mail transfer agent and the install appears to have created user accounts for the qmail daemon (qmaild), among other things. I don't use qmail myself, so I don't know of this is normal or not.

---

### Post by 2F4U on 2012-07-31
It is not uncommon that applications that run as a service/daemon install their own user account. This is to prevent these daemons to run as root, which can be dangerous. It is also common that such accounts are not able to login.

---

### Post by Ben Neville on 2012-07-31
I must say I am very impressed with the Ubuntu Community
You guys are fantastic. Thanks for the responses!

I'm reinstalling ALSA now to check the sound problem and I'll uninstall qmail if I can find it, Don't even know how it got on here.

Thankyou!!

---

