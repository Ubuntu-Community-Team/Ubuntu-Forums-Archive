---
title: "browser crash with segfault"
date: 2009-10-14
forum: General Help
---

### Post by copyhold on 2009-10-14
he||o all.
I have an Apache installed on my local machine with a few hosts configured.

so, Chromium,,opera, midori... all of them crushes wif segmentation fault when i try to access those local sites.

FF is 0k.

dmesg says after crash:
```
[1118354.872921] midori[15971]: segfault at b4aa20bc ip b6c16a95 sp b4aa20a4 err
or 6 in libc-2.9.so[b6b4f000+15c000]
[1122093.378538] chromium-browse[17906]: segfault at b4f9c0fc ip b7066a95 sp b4f
9c0e4 error 6 in libc-2.9.so[b6f9f000+15c000]
```


forgot 2 mention - browsing with no problem over other (not local) sites.

---

### Post by wmarin on 2009-10-14
It is the browser or Apache who is crashing?
Maybe related to [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/343870]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/343870")
Good luck!
wmarin

____________________________________________---
Forgot to mention, just in case it is Apache+php  causing the segfault, This should be fixed now with the updated php5-suhoshin in the archive now, according to: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/418897]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/418897") ).
The same post gives you a temporary fix.

In case this has nothing to do with your question, just ignore me.....(just trying to help).

Best regards,
wmarin

---

### Post by copyhold on 2010-01-27
> It is the browser or Apache who is crashing?

browser only, Apache is OK.

---

