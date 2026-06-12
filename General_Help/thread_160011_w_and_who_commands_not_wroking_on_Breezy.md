---
title: "w and who commands not wroking on Breezy"
date: 2006-04-14
forum: General Help
---

### Post by z_diver on 2006-04-14
Not sure if anyone else has this issue but I cannot get the w and who commands to show who is logged in properly.  For some reason they only display the first user logged on.

Anyone have suggestions?

---

### Post by z_diver on 2006-04-15
Update:
I've tested this on 4 Ubuntu machines now....3 Breezy and 1 Dapper.  None are working correctly.  Who just returns info on the first two sessions and w none.

Is anyone able to get an accurate list of login sessions when running:
```

>$ w 
[COLOR="Red"]or[/COLOR]
>$ who
```

---

### Post by krismatth3 on 2006-04-15
I have no trouble getting a full listing on the two systems at my disposal (5.10).

---

### Post by astoltz on 2006-04-15
No problem here either.  I had everyone logged on via the local terminals though (tty1, tty2... no ssh sessions).  I have had who (and w) tell me that a user was logged on when in fact they weren't.  I'm sure there are better ways to fix it, but I usually drop to single user mode (sudo telinit 1), then back to the default run level (telinit 2).

---

### Post by dcstar on 2006-04-15
[QUOTE=z_diver]Update:
I've tested this on 4 Ubuntu machines now....3 Breezy and 1 Dapper.  None are working correctly.  Who just returns info on the first two sessions and w none.

Is anyone able to get an accurate list of login sessions when running:
```

>$ w 
[COLOR="Red"]or[/COLOR]
>$ who
```[/QUOTE]
These sort of problems are usually the result of corrupted /var/run/utmp or /var/log/wtmp files, or - as the utmp man page says:
```
       Note that the utmp struct from libc5 has changed in libc6.  Because  of
       this,  binaries  using  the old libc5 struct will corrupt /var/run/utmp
       and/or /var/log/wtmp.  **Debian systems include  a  patched  libc5**  which
       uses  the  new  utmp  format.  The problem still exists with wtmp since
       it's accessed directly in libc5.
```
So, if you have installed some package that has overwritten the original libc5, then you may have problems in this area.

---

### Post by z_diver on 2006-04-16
[QUOTE=dcstar]
So, if you have installed some package that has overwritten the original libc5, then you may have problems in this area.[/QUOTE]
Hey, thanks for the test results you guys!  I also got a positive result on a dapper machine today so it must be that I have installed something similar on all of the machines in question.  

David -- thanks for the info above, it seems to be either build-essentials or beep-media-player-dev that has caused me to upgrade libc6(there is not a libc5 installed) to version 2.3.5-1ubuntu12.5.10.1(breezy-updates) instead of the regular 2.3.5-1ubuntu12(breezy) version.  This was determined by trying to force version and seeing what files it wated to remove so I'm not sure it's accurate.  At this point i think I can live without the media player package but not without build-essentials so if I have to choose, I'll stay put.

Big THANKS to everyone that's looked into this boring topic. :D

---

