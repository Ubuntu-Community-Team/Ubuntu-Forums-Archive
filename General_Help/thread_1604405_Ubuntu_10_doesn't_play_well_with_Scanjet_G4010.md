---
title: "Ubuntu 10 doesn't play well with Scanjet G4010"
date: 2010-10-24
forum: General Help
---

### Post by tbplayer on 2010-10-24
This weekend I installed Ubuntu 10.10 and most everything works well, but it seems that there is no support for my scanner, an HP Scanjet G4010. Both lsusb and sane-find-scanner report the scanner, and I've changed the permissions of the appropriate USB device, but scanimage -L returns "no scanners were identified" and the HPLIP Toolbox cannot find the scanner. Additionally, the Sane site states that it's unsupported. So I'm just posting here as the final resort to see if there is anyone who has a fix or who has been able to get this scanner working - if so, please share!

Thanks.

---

### Post by lars.m on 2010-11-03
Try running "sudo scanimage -L"
if that works it an access rights issue:
system->administration->users->advanced->user privileges
Check that "use video devices" are enabled.

I got my G4010 running using the above and the beta/development version of the sane backend. You can get it here:
[http://git.debian.org/?p=sane/sane-backends.git](http://git.debian.org/?p=sane/sane-backends.git)

Since I downloaded and compiled the beta/dev version first, and then later found out I had a rights issue I do not know if the official release will work for you.

Hope this helps...

---

