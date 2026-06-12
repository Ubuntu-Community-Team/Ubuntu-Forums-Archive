---
title: "Anydoby know where the clamav engine is hosted now?"
date: 2011-07-20
forum: General Help
---

### Post by stevennlv on 2011-07-20
>                                   **Re: How to upgrade ClamAV engine regularly and automatically?**             
                                                                Try this one ;

echo deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free >> /etc/apt/source.list

and then apt-get update
after that apt-get upgrade clamav

and if you having problem sample :

The following packages have been kept back:
  clamav clamav-freshclam libclamav3
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

then do this command :
aptitude full-upgrade

It will automatically upgrade your clamav library.

Done.. now your clamav is already using the latest update :smile:.
test your clamav with this command :

clamscan --version

I hope that help.
Cheers,
Fmuhandi I've got clamav installed and configured. But for the life of me I can't get the engine to upgrade. I've tried 5 or 6 "solutions" from the forums. But none has worked.

I found this one from fmuhandi in response to a post back in '08. All the others just flat out failed. This one is getting 404 errors.

Any body know what the current addy is or have a better solution?

---

### Post by stevennlv on 2011-07-20
Never mind. I combined two solutions and made it work. I'm hard headed that way!

---

