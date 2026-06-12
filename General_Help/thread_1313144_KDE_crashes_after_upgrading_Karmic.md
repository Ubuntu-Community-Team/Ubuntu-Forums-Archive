---
title: "KDE crashes after upgrading Karmic"
date: 2009-11-03
forum: General Help
---

### Post by raulih on 2009-11-03
After upgrading to Karmic all KDE apps started crashing (digikam, konqueror). Tried clean re-install, still crashing. Tried creating a new profile... suprise, everything works in that profile. 

What kde-specific directories/files I should try deleting from my profile directory to reset everything? I tried deleting .kde but that doesn't help.

This could be related to file browsing since in digikam crash happens when selecting directories to include, and running conqueror from terminal did show wine-related error. However uninstalling wine didn't help, only removed those errors.

---

### Post by raulih on 2009-11-06
I tried to remove and reinstall all KDE related packages but no help. Does anyone know about this? I use 64-bit Ubuntu (Gnome).

---

### Post by raulih on 2009-11-06
Running digikam from terminal shows only

```
$ digikam
kbuildsycoca4 running...
KCrash: Application 'kbuildsycoca4' crashing...
sock_file=/home/rauli/.kde/socket-koala3/kdeinit4__0
ERROR: Running KSycoca failed.
```

where second line appears when pressing directory browse icon to select locations to include in database. When "Select folder" windows open, the errors i get are "URL cannot be listed file:///" and "Malformed URL" and several KBuildSycoca pop up windows that don't provide useful crash information. Unable to show any directory content or browse directories. Same errors are shown in all kde apps.

I also got KBUildSycoca errors twice while *installing* K3B with all it's dependencies. Installation did go through and there was nothing special in terminal log.

---

### Post by raulih on 2009-11-06
Opened bug [https://bugs.launchpad.net/ubuntu/+bug/476719](https://bugs.launchpad.net/ubuntu/+bug/476719)

---

### Post by raulih on 2009-11-07
Copying and replacing *~/.local/share/mime* directory from the new account i created to my main account fixed this.

---

### Post by digibill on 2010-01-25
> **raulih said:**
> Copying and replacing *~/.local/share/mime* directory from the new account i created to my main account fixed this.

This also worked at my case: I deleted the mime directory and now Digikam loads and works!
Thanks!

---

