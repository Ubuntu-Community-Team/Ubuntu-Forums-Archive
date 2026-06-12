---
title: "disable compiz on one monitor in a two monitor system"
date: 2010-02-23
forum: General Help
---

### Post by odror on 2010-02-23
I have persistent video tearing my second monitor (Mitsubushi HDTV). I have tried everything that was suggested with some improvement. I have no issue with tearing if I add the following to my xorg.conf
> 

Section "Extensions"
    Option         "Composite" "Disable"
EndSection


Is it possible to disable composite for one monitor only and keep it for the other. Or at lease is it possible to have compiz for one monitor only and disable it for the other.

-Thanks.

---

### Post by harrisonk on 2010-02-23
[SIZE=2]Hello

From what I can think of you can't change it, at least not with out a lot of coding.

Anyone please correct me if I am wrong.

Harrison
[/SIZE]

---

### Post by odror on 2010-02-23
Ok in that case is their a command line that can be used to enable or disable compiz.

If there is one. Can I get mplayer to stop compiz when it plays a movie and start compiz when it stops playing

-Thanks

---

