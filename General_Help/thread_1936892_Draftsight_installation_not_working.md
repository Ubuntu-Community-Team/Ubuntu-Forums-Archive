---
title: "Draftsight installation not working"
date: 2012-03-06
forum: General Help
---

### Post by Mrenief78 on 2012-03-06
Hi,
 I've had DraftSight installed and it was working for a year.
I didn't renew the licence in time and I couldn't find out how to get it started again. 
So I just removed it and thought - well I'll just install it again from new..
Well... When I tried to install it - I get this message:
(Reading database ...  (Reading database ... 5% (Reading database ...  10% (Reading database ... 15% (Reading database ... 20% (Reading  database ... 25% (Reading database ... 30% (Reading database ... 35%  (Reading database ... 40% (Reading database ... 45% (Reading database  ... 50% (Reading database ... 55% (Reading database ... 60% (Reading  database ... 65% (Reading database ... 70% (Reading database ... 75%  (Reading database ... 80% (Reading database ... 85% (Reading database  ... 90% (Reading database ... 95% (Reading database ... 100% (Reading  database ... 350976 files and directories currently installed.) 
Unpacking dassault-systemes-draftsight (from .../mike/Downloads/draftSight.deb) ... 
No protocol specified 
No protocol specified 
 
Gtk-WARNING **: cannot open display: :0.0 
dpkg: error processing /home/mike/Downloads/draftSight.deb (--install): 
 subprocess new pre-installation script returned error exit status 1 
Errors were encountered while processing: 
 /home/mike/Downloads/draftSight.deb 

any idea what the problem could be?
I am now on 12.04 but had the same problem last week when it was still 11.10.
Thanks,
Mike

---

### Post by Mrenief78 on 2012-03-06
Solved it by using
sudo dpkg -i --force-architecture DraftSight.deb
in terminal.

---

### Post by ginger5xm on 2012-04-23
Hi,

Installed on 3 Ubuntu 32 bit machines.  Works like a charm on first 2, for last couple of months.  On 3rd machine will only run as root.  Noticed that Gdebi installed files with Root as owner and rights, but I installed it from my account.  Tried changing access permission to include my account, and applied to all files below /opt/dass....  but to no avail.

What to do?  Thx!

---

### Post by abhio on 2012-04-26
Pretty much the same problem. I'm running draftsight on 64 bit Ubuntu 10. Draftsight was running happily until I removed openoffice and installed libreoffice. After that, it would simply not start. So I removed draftsight with dpkg -p. Unfortunately, I'm unable to re-install.

```
sudo dpkg --force-architecture
```gives:

```
/var/lib/dpkg/tmp.ci/preinst: line 21: /var/lib/dpkg/tmp.ci/ShowLicence: No such file or directory
```Any ideas?

---

