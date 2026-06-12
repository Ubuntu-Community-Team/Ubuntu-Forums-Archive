---
title: "Dpkg Issues"
date: 2010-01-02
forum: General Help
---

### Post by Dr Belka on 2010-01-02
Sorry about the title of this thread, I wasn't quite sure how to provide a descriptive title.  Im sure this is an easy problem to solve for someone more familiar with dpkg than me.  So I was installing something, usplash, I think it was...

I ran $ sudo aptitude install usplash

and after it asked me if I wanted to install some aditional packages, it returned this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I have seen this error before.  I just ran the command
$ sudo dpkg --configure -a

and it returned this:
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28.10-some-string-here
Cannot find /lib/modules/2.6.28.10-some-string-here
update-initramfs: failed for /boot/initrd.img-2.6.28.10-some-string-here
dpkg: subprocess post-installation script returned error exit status 1


I did an:
$ aptitude search initramfs-tools
and I noticed that it had a "C" next to it.  I think this has something to do with the package not being configured correctly or at all.  Also looks like it is trying to generate an initd, but missing something.  That kernel name looks kinda funky, though...

Anyone have a suggestion?

---

### Post by Dr Belka on 2010-01-02
bump 1/2

---

### Post by Dr Belka on 2010-01-03
bump 2/2

please help

---

