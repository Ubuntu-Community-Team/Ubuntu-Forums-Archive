---
title: "Root processes so sloooow"
date: 2006-04-04
forum: General Help
---

### Post by Dafydd on 2006-04-04
Hello,

If I type 'gksudo gedit filename' then gedit will open but after 3-4 minutes. The same goes for nautilus, or any other programme opened as root.

If I open gedit or nautilus as a normal user then everything is fine. The programs open after 2-3 seconds.

What can I do to speed things up? 

Running Breezy, I get the following error message:

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Thanks for any help!

Dafydd

---

### Post by mark_g on 2006-04-04
I'm not sure, but it's possibly because you cannot login as root by default in Ubuntu. Might be the reason why authentication is rejected.
You can enable it by doing the following and see it solves your problem.

From [http://ubuntuguide.org/#allowrootlogingnome](http://ubuntuguide.org/#allowrootlogingnome) :

   1. System -> Administration -> Login Screen Setup
   2. Login Screen Setup

Security Tab -> Options -> Allow root to login with GDM (Checked)

---

### Post by Dafydd on 2006-04-04
[QUOTE=mark_g]I'm not sure, but it's possibly because you cannot login as root by default in Ubuntu. Might be the reason why authentication is rejected.[/QUOTE]

Thanks. Tried this but still get the authentication problem and gedit/nautilus still take 2-3 mins to open from xterm/terminal. I suppose I could log in as root to gdm to do all the things I need to then log out... but ...

Does anyone know anything else?

I've had nothing but problems with Ubuntu for the past few days. Cannot install my webcams (motioneye + spacecam 120), then after trying all the modules (including mouse + ipw2200) seemed to disappear... So reinstalled ... and am still having problems. 

Cheers
Dafydd

---

