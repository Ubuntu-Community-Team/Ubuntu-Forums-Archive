---
title: "mouse not working in 12.04"
date: 2012-10-06
forum: General Help
---

### Post by badperson on 2012-10-06
This is a new issue, the mouse works fine in my win partition and when booting into older versions of linux kernel. 

when running software updates, I am unable to install, I get an error saying the installation or removal of a package failed.

Not sure if there is a connection there at all. 

It had honestly been awhile since I had booted into ubuntu; the only thing I can think of is that I tried to connect an external HD, and it wouldn't start up...but that was in windows. 

Can't imagine what the problem is. Was hoping the updates would fix it...anyone else have that issue?

> 
$ uname -a
Linux  3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux




this is the reason for the fail, according to the update app: 

> Changes for the versions:
Installed version: 1.4.18-1ubuntu1.1
Available version: 1.4.18-1ubuntu1.3

Version 1.4.18-1ubuntu1.3: 

  * REGRESSION FIX: some applications launched with the activation helper
    may need DBUS_STARTER_ADDRESS. (LP: #1058343)
    - debian/patches/CVE-2012-3524-regression-fix.patch: hardcode the
      starter address to the default system bus address.
  * REGRESSION FIX: unclean shutdown after dbus upgrade (LP: #740390)
    - debian/libdbus-1-3.postinst: trigger an upstart re-exec before
      shutdown or reboot so that it can safely unmount the root
      filesystem.


how do I run those utils? never run that kind of stuff before.

---

### Post by badperson on 2012-10-06
any links to docs explaining how to apply patches?

---

### Post by badperson on 2012-10-06
also tried to re-install dbus manually, and got this: 

```
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 linux-headers-3.2.0-24 libglew1.5
  linux-headers-3.2.0-24-generic liboil0.3:i386 libglewmx1.5
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  dbus
1 upgraded, 0 newly installed, 0 to remove and 87 not upgraded.
Need to get 0 B/358 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `linux-headers-3.2.0-31-generic' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by badperson on 2012-10-16
bump...
anyone ever come across that empty headers issue? 

I googled some more and found [this link]("http://www.richud.com/wiki/Ubuntu_Dpkg:_unrecoverable_fatal_error"), but when I try to boot into the newest ver of linux, i get an error to the effect of, gave up waiting for root device. It goes into a shell. I can still boot into a prev version of linux, which I guess is ok...hoping a new update will wipe out this issue. 
bp

---

### Post by badperson on 2012-10-16
ok (kind of having a conversation with myself here, but thought someone else might come across this issue...)

I booted into a prior version of linux (after getting the error described above) and did updates from there. I then rebooted normally and everything is now ok.

---

