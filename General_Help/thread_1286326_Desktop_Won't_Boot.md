---
title: "Desktop Won't Boot"
date: 2009-10-08
forum: General Help
---

### Post by lotusalive on 2009-10-08
Hi !  Silly me !  I'm embarrassed to ask what I've done, but maybe someone will tell me what software 'wires' I might have crossed to prevent me from doing this again in the future, that is, if any of this makes sense to anyone, since I'm lost !  I did look at the other post on Desktop Won't Boot but none of those commands worked for me either...

I have loaded 2.6.28-15-server, and generic, and 386-generic kernels.

Currently grub hangs half-way through boot.  Some of the many differing error msgs are as follows:

a)  Recovery: dpkg: 
W: Failed to fetch [http://us.archive.ubuntu.com/dist/jaunty-security/Release.gpg](http://us.archive.ubuntu.com/dist/jaunty-security/Release.gpg)  Could not resolve 'us.archive.ubuntu.com', and same is true of /jaunty-backports and medibuntu.org


b)  Pidfile not found.  Is jackd running?  (jackd is not installed)

c)  Warning: mistmatch between OSS & version of kernel

d)  [14.677927] hda_codec: Unknown model for ALC883 trying auto-probe from Bios

e)  Starting automounter: loading autofs4 kernel module,WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

f) sudo su (to root, p/w) gives msg: pam_mount (pam_mount .c100): unknown pam_mount option "use_first_pass"

g)  also at root term input: /etc/fstab  AND /etc/mtab reply with Permission denied.

I apologize for dumping this on you guys, but if anyone understands what I might have done, beyond the obvious of loading OSS and my Intel GC not handling it, it would be greatly appreciated.

---

