---
title: "Indicator Updates Causes Errors at Start-Up [OAFIID:GNOME_FastUserSwitchApplet]"
date: 2010-03-07
forum: General Help
---

### Post by navneeth on 2010-03-07
This error has been recorded many times before as a Google search will show, but all those reports were for earlier versions of Ubuntu whereas I use 9.10.

> The panel encountered a problem while loading "OAFIID:_FastUserSwitchApplet.

Delete Don't Delete.

There were a lot of updates for indicator applets yesterday, and this error showed up after the first reboot after these updates were installed. (Please go through the attached file from dpkg.log for the files that were installed.)

Oh, and the packages gnome-applets and gdm are "already installed and the newest versions."

---

### Post by navneeth on 2010-03-07
[After a while...]

Now the error message does not pop up when the desktop appears, but I notice that the System menu has three new options which were removed in 9.04 -- **Lock Screen**, **Log Out <username>...**, and **Shutdown...**!

This is strange.

---

### Post by Endolith on 2010-03-22
> **navneeth said:**
> [After a while...]

Now the error message does not pop up when the desktop appears, but I notice that the System menu has three new options which were removed in 9.04 -- **Lock Screen**, **Log Out <username>...**, and **Shutdown...**!

This is strange.

Yes, this happens for me when fast switcher doesn't work.  The same options show up in System instead.  This is certainly good, because otherwise you wouldn't be able to access them.  :)  I don't know why the fast user switcher isn't loading.  

For me this problem only happens on first boot.  Every applet says "encountered a problem".  If I then log out and log back in, it works.  I don't know why, but it happens every time.  :(

---

### Post by M@se on 2010-04-03
Just got this error message myself. Since installing 9.10 have not been able to even get past the login page

---

