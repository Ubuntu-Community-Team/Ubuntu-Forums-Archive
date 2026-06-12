---
title: "Roll back recent update"
date: 2010-07-08
forum: General Help
---

### Post by KLStringer on 2010-07-08
I think a recent update has broken 2 of the 3 systems that I've been putting together. To test out the theory I want to roll libpam-modules back to version 1.1.1-2ubuntu2 from 1.1.1-2ubuntu5 that was recently released on 1 of the 2 that got updated and see if it resolves the issue that I'm seeing with not being able to log into the OMSA webserver.

How do I go about reverting to the earlier version?

---

### Post by KLStringer on 2010-07-08
Being that the underlying problem with OMSA is that on a x64 system you have to use the x32 pam files for libpam-modules ([https://subtrac.sara.nl/oss/omsa_2_deb/wiki/FAQ#Noteforamd64](https://subtrac.sara.nl/oss/omsa_2_deb/wiki/FAQ#Noteforamd64)) I've been trying to find a download for libpam-modules_1.1.1-2ubuntu5_i386.deb but haven't been able to locate it at [http://packages.ubuntu.com](http://packages.ubuntu.com).

Is there somewhere else that I can look for it at?

---

### Post by KLStringer on 2010-07-08
Found it here, testing now to see if it solves the issue, will replay back momentarily 

[http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5_i386.deb)

---

### Post by KLStringer on 2010-07-08
Still cannot remotely log into OMSA

---

### Post by KLStringer on 2010-07-08
Switched gears in my troubleshooting and tried to log in from a different station and I can log into all 3 servers without any problems. I'm gonna go ahead and say that the issue isn't with the servers or OMSA but with either Firefox or the MS box that I use.

What's weird is everything worked great last night before I went home, then today the boss came back from vacation and he wanted me to show him that it was working and I couldn't log into 2/3 of the servers.

---

