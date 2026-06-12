---
title: "configure gppp for many isp telephone numbers"
date: 2006-04-10
forum: General Help
---

### Post by ubunlilluz on 2006-04-10
hi,
i've a 56k flat that it works only at night. In the day i connect by another isp.
I've set my modem by wvdial and connect by gppp. The problem is that with this system i've managed to set only one connection to the night isp, because gppp
can save many isp telephone numbers, but not many couple login/password.
Have Somebody solved this problem?

---

### Post by towsonu2003 on 2006-04-10
have a look at ```
man wvdial
``` you can put new phone numbers and usernames/pass as new sections to wvdial.conf and use ```
sudo wvdial sectionname
``` to dial with these. Just experiment ;) I never tried that, hence the man wvdial suggestion :)

---

