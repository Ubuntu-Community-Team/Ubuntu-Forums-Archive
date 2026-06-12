---
title: "Today's update failed"
date: 2010-08-24
forum: General Help
---

### Post by jfbooth on 2010-08-24
First, I apologize if I am committing an infraction .. I posted this in another category (INSTALLATIONS AND UPGRADES) but it is not getting any answers there.  I am using XUBUNTU 10.04 and today, update manager said there were several updates available.  I started the process but during some of the updates, one of them 'errored'.  Here is what I posted:

Update manager says "Updates are available
linux-image-2.6.32.24-generic
Linux kernel image for version 2.6.32 on x86/x86_64 (30.0MB)"

Process fails .. errors all over the place .. some are listed:

"E: /var/cache/apt/archives/linux-image-2.6.32-24-generic_2.6.32-24.41_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2"

"Sub-process /usr/bin/dpkg returned an error code (1)
a pkg failed to install. Trying to recover:"

and I wait ... no drive activity .. and wait, then I cancel. Try whole thing again, same failure(s).

I looked in /var/cache/apt/archives/ and linux-image-2.6.32-24-generic_2.6.32-24.41_i386.deb is there. Thought if I deleted it, it might solve the problem .. but it comes back read only. Also, I notice it is NOT a .tar file ... am a NOOB, so not sure if I am on the right track. Maybe it is a bug in the update rather than a problem on my computer. Noob .. don't know much .. need help. Thank you in advance.

---

### Post by jfbooth on 2010-08-25
I THINK I fixed it.  I deleted linux-libc-dev_2.6.32-24.41_i386.deb from /var/cache/apt/archives and tried the UPDATE again.  Appeared to install OK .. so I guess all is well.  Hope this helps someone else with a similar problem.

---

