---
title: "Can't update. (Karmic)"
date: 2010-05-25
forum: General Help
---

### Post by Scooter_X on 2010-05-25
Here's what the update manager tells me:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://packages.universal.org/dists/karmic/Release.gpg](http://packages.universal.org/dists/karmic/Release.gpg)  Could not resolve 'packages.universal.org'

W: Failed to fetch [http://packages.universal.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://packages.universal.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.universal.org'

W: Failed to fetch [http://packages.universal.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://packages.universal.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.universal.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
...what in the heck does THAT mean?!

---

### Post by mac9416 on 2010-05-25
Hi, Scooter_X,

It appears that your software sources point to a server that is not up: packages.universal.org. You should go to System > Administration > Software sources and change the mirror.

---

### Post by Scooter_X on 2010-05-27
Yeah, I've tried a few different mirrors, and still the same error pops up. What's the part about the "NO_PUBKEY 2EBC26B60C5A2783" mean, do you know? Am I missing something that I should have in order to make my updates work?

---

### Post by mac9416 on 2010-05-27
Someone else might be better able to explain that error than I am. But if I understand correctly, that error has to do with a security feature of the Medibuntu repository that isn't completely set up on your machine. I don't believe the error is serious, and it certainly isn't causing the "Failed to fetch" errors.

I'm surprised that no other mirros work. Could you post the contents of your /etc/apt/sources.list file?

---

### Post by DellNote on 2010-05-28
Hello,

I just solved this in lucid.  The post is:
[http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error-3.html](http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error-3.html)

It describes a number of changes I made, the sum of which solved the problem.  I believe the last one was the critical one:

I had an EXTRA copy of libreadline.so.6 in /usr/local/lib that was apparently fouling up the whole apt/updater chain since it wasn't the same as the other copies in the system.

The solution for me was to DELETE the copy of libreadline.so.6 in /usr/local/lib and REPLACE it with a LINK to /lib/libreadline.so.6

Good Luck

---

### Post by Scooter_X on 2010-06-05
> **DellNote said:**
> Hello,

The solution for me was to DELETE the copy of libreadline.so.6 in /usr/local/lib and REPLACE it with a LINK to /lib/libreadline.so.6

Good Luck

Thanks for your post, DellNote. I found that I didn't even HAVE libreadline.so.6 in /usr/local/lib, but I put a link in there all the same. I copied the 'libreadline' file from another Karmic system into the Karmic system that wasn't updating. All the same I got the goofy error... Oh well. I just backed up what I needed and started over. It weirds me out but that's life. Thanks again.

-Scooter

---

