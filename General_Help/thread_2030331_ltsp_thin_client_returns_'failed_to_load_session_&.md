---
title: "ltsp thin client returns 'failed to load session &quot;Ubuntu&quot;"
date: 2012-07-20
forum: General Help
---

### Post by JayKay3OOO on 2012-07-20
_Synopsis_

[I]Ubuntu Server 12.04

AMD Zacate E350 fusion dual core processor based machine

LTSP installed via this [http://www.youtube.com/watch?v=8yD0QV_Cm2w&feature=my_liked_videos&list=LLTYLnEPDK8IeaU-k1g0g0qw](http://www.youtube.com/watch?v=8yD0QV_Cm2w&feature=my_liked_videos&list=LLTYLnEPDK8IeaU-k1g0g0qw) video the commands are the same through the versions.

SSH running and tested working (i.e, I'm connected to the Ubuntu server machine via putty SSH from W7)

DHCP 'works'. I'm not sure if I have the right config, but the thin client (a 2.3GHZ 2GB ram 15.4 inch laptop with no hard drive boots to the login, so does my quad core phenom 2)

Can login to the terminal (ctrl+alt+f1) having made a root pass.

webmin is also installed.

[/I]

_Problem_

[LIST=1]
[*]Can't use familair name for SSH or Webmin so using IP at the moment. Hosts & hostname filled in.

[*]From thin client (i.e network boot) graphical login session returns 'failed to load session "Ubuntu"'

[*]Unsure how to add a different window manager as thin client still gives same list even when different manager selected.
[/LIST]

Priority is to get a login working.

Cheers.

---

### Post by JayKay3OOO on 2012-08-24
Well. I can mark this as solved.

Thanks for all the help :p You guys were great! No one wins a cookie this time.

Anyway, after getting nowhere I tried the simplest of things after making the original post. I installed gnome DE (Desktop Environment) straight onto ubuntu server and shzam! The default buntu still throws the original error, but it works in XFCE and gnome without the effects.

Guess that'll teach me for being a noob.  

Result? Laptop with no hard drive can connect to ltsp server and run XFCE or gnome DE with minimal lag and full functionality with users seeming to have their own workspace and home folders. My other phenom 2x4 machine can connect to same ltsp server as different user and two users can have comparable experiences from the limited power of the e350 fusion chip. OFC a real world setup would more likley feature the phenom2 box in a 30+ office setup.

Now to go implement this in Win server!):P

---

