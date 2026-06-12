---
title: "Firefox crashed on upgrade"
date: 2011-01-29
forum: General Help
---

### Post by Jim@coast on 2011-01-29
Hi,

Since upgrading from 10.04 to 10.10 Firefox crashed on rebooting the computer at the end of installation.  I get the following message: "Firefox had a problem and crashed. We'll try to restore your tabs and windows when it restarts."  I searched this forum and found no mention of the problem.  I really don't want to continue using Chrome.  Any thoughts?

The details are:
Add-ons: {d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}:1.3.3,{0545b830-f0aa-4d7e-8820-50a4629a56fe}:4.6.5,{b9db16a4-6edc-47ec-a1f4-b86292ed211d}:4.8.2,{ef4e370e-d9f0-4e00-b93e-a4f274cfdd5a}:1.4.1,foxyproxy@eric.h.jung:2.22.5,{73a6fe31-595d-460b-a920-fcc0f8843232}:2.0.9.6,{89736E8E-4B14-4042-8C75-AD00B6BD3900}:1.0.5,ntortarolo@hotmail.com:2.7.2,ubufox@ubuntu.com:0.9rc2,{2e17e2b2-b8d4-4a67-8d7b-fafa6cc9d1d0}:1.2.5.1,{a0d7ccb3-214d-498b-b4aa-0e8fda9a7bf7}:20100908,langpack-en-GB@firefox-3.6.ubuntu.com:3.6,adblockpopups@jessehakanen.net:0.2.1,langpack-en@firefox-3.6.ubuntu.com:3.6,langpack-en-CA@firefox-3.6.ubuntu.com:3.6,langpack-en-AU@firefox-3.6.ubuntu.com:3.6,{a03390fe-612a-4cfb-9861-ce9369d54a0b}:0.1.1,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.6.13
BuildID: 20101206121845
CrashTime: 1296285940
EMCheckCompatibility: true
Email: [email]jmcdonald@jmcdonald.infno[/email]
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1296188357
ProductName: Firefox
ReleaseChannel: default
SecondsSinceLastCrash: 68
StartupTime: 1296285937
Theme: classic/1.0
Throttleable: 1
URL: about:blank
Vendor: Mozilla
Version: 3.6.13

---

### Post by Krytarik on 2011-01-29
If you suspect a faulty installation of Firefox, try re-installing it:
```
sudo apt-get install --reinstall firefox
```
You may also, and even before, try disabling *all* extensions, and if Firefox works after that, re-enable one after each other.

---

### Post by peculiar penguin on 2011-01-29
Try safe mode (run firefox -safe-mode in a terminal) or creating a new browser profile (firefox -P).

---

### Post by Jim@coast on 2011-01-30
Sorry none of these options worked. Thanks anyway.

---

### Post by Jim@coast on 2011-01-30
Managed to reinstall and clear profile but still having problems, especially if I try to set my preferences.  But it is unworkably unstable still....

---

### Post by Krytarik on 2011-01-30
You may try one of those options:
[http://ubuntuforums.org/showpost.php?p=10395236&postcount=4](http://ubuntuforums.org/showpost.php?p=10395236&postcount=4)

I would personally try the simple manual "install", it wouldn't change anything any is easyly removable. I'm curious if that works better than the official package.

EDIT: What do you by "reinstall"? Hopefully just Firefox!

---

