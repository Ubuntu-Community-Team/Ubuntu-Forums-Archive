---
title: "kubuntu 10.04 KDE Panel restore"
date: 2010-05-02
forum: General Help
---

### Post by Squallo on 2010-05-02
I deleted my "task bar" panel that is at the bottom of the screen and I can't figure out how to restore it in this version.  I've searched the forums and the answers for previous versions of Kubuntu don't seem to work for me.  Is there anyone who has solved this problem after downloading version 10.04.  Thanks for your help

---

### Post by mjthfx on 2010-05-06
Me too! Is there an easier way than rebuilding the panel??

Please help. Thanks

---

### Post by Zorael on 2010-05-06
Well, you could delete the settings file and have it recreate itself.
```
$ kquitapp plasma-desktop
$ rm ~/.kde/share/config/plasma-desktop-appletsrc
$ plasma-desktop &>/dev/null
```
Or, in one line for easy copy/pasting;
```
kquitapp plasma-desktop; rm ~/.kde/share/config/plasma-desktop-appletsrc; plasma-desktop &>/dev/null
```
Just paste that in a terminal.

edit: As a sidenote, they're adding templates in future versions of Plasma. With those you could just add a Default Panel and it'd look as it did at first login.

---

### Post by leeds_shrew on 2010-07-12
Thank you! 

OP: Please mark his thread solved.

---

### Post by pbvijay on 2010-10-03
Hi,Its helped me too to resolve the panel issue. thank you
Now Empathy and other tray application functions correctly
Thx
Vijay

---

### Post by xiqqix on 2010-10-19
thanks a lot :)

---

### Post by iserdem on 2012-02-09
thanks

---

### Post by Stubbs3 on 2012-04-30
Thank You!\\:D/

---

### Post by oldos2er on 2012-05-01
Old thread closed.

---

