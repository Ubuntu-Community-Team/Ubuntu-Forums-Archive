---
title: "Can't Login - &quot;Module Not Found&quot;"
date: 2009-11-01
forum: General Help
---

### Post by joey-elijah on 2009-11-01
I'm currently unable to login to Karmic. On the GDM screen i'm presented with the usual image however when clicking on my name there is no password field, instead it simply says "module not found."

If i hit Alt+F2 and try to log in it goes mad, repeatedly telling my i've exceeded the incorrect password limit. 

What would i need to reinstall to fix this? I assume just the GDM package? How would i install it when even the command prompt won't let me log in?

---

### Post by Juno360 on 2009-11-07
I had the exact same problem on 64-bit karmic after installing and removing fingerprint login.

I actually found a thread when I was in windows but I can't seem to find it now.

Anyway here are the instructions:

login to recovery mode with networking in ubuntu (will automatically log you on to root):

dpkg --force-all ---purge libpam-runtime
dpkg --force-all ---purge libpam-modules

rm -rf /etc/pam.d
rm -rf /lib/security

apt-get install libpam-runtime libpam-modules

reboot now

---

### Post by Noahod on 2009-12-18
Thanks, solved it for me too.

---

### Post by iokhahon on 2011-05-30
> **Juno360 said:**
> I had the exact same problem on 64-bit karmic after installing and removing fingerprint login.

I actually found a thread when I was in windows but I can't seem to find it now.

Anyway here are the instructions:

login to recovery mode with networking in ubuntu (will automatically log you on to root):

dpkg --force-all ---purge libpam-runtime
dpkg --force-all ---purge libpam-modules

rm -rf /etc/pam.d
rm -rf /lib/security

apt-get install libpam-runtime libpam-modules

reboot now

[Solved] I had the exact same problem today, I am not entirely sure what caused it, the only significant change I recall doing was installing a bunch of packages to enable me to build Alien Arena.

These instructions really saved my bacon, I  appreciate the Ubuntu community members who take the time to post this kind of information. Thank you all so much, keep it up!

---

### Post by miro-kolar on 2011-06-17
Hi!
I have a similar problem, in newly installed natty. libpam-modules and libpam0g are not properly installed (in synaptic, no installed files are displayed for these two packages, in spite of being "successfully" installed; /lib/security has not files from libpam-modules).

I have tried the above procedure, it did not help to correct my problem.

Any other suggestions.

Thanks

---

### Post by miro-kolar on 2011-06-17
My problem was apparently caused by a misspelling in /etc/pam.d/slim that I added manually. ;)

Everything now seems to work OK in spite of the fact that /lib/security now (after I reinstalled a number of libpam.... modules as suggested by iokhahon) contains just a single file, and in synaptic I am still getting for supposedly installed libpam-modules and libpam0d message "The list of installed files is only available for installed packages"!

---

