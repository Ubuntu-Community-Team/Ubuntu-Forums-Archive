---
title: "two versions of openoffice?"
date: 2009-07-08
forum: General Help
---

### Post by jamaas on 2009-07-08
I'm running 9.04 on a eeepc 901 with limited disk space but it runs quite well.  I'm trying to reduce/remove some application and seem to have two different versions of openoffice loaded?

Synaptic shows me (eg.)

openoffice.org 1:3.1.0-5ubuntu1-jaunty1

as well as

openoffice.org3   3.1.0-11

are these different versions or the same thing?  I have tried to install directly from sun to get updated versions ... have I goofed?

Thanks

Jim

---

### Post by darolu on 2009-07-08
Yes it is the same version, distros like Ubuntu include "customization" (branding) stuff to its applications, if you look the package name you'll see after the full colon it says the same version "3.1.0".

If you want the latest updates you may want to try PPA repos; to do it add this repositories to your **/etc/apt/sources.list** file, you'll have to edit as root (or with sudo):
```
gksu gedit /etc/apt/sources.list
```
and paste this lines at the end of the file:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
```

You'll also need the 'key' for this repositories; on a text file copy and paste this and save as "office.key":
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXanRwEEAOTPu1sTcJChTjkA9LkIh6WqiBgPzxNY2p8w18Qt/cE3ev4VyjiIadZtr+fh
C+kuRRQuRinLV+MzeD7Od3uqyR1plc90lqUeLeKJMgXfCoGMmKwng0qD2gpevIvEEpdlmsRo
1hutsyRxAL3o/NfFpovg6dWC27Y1Vwwma8UIL5wXABEBAAG0K0xhdW5jaHBhZCBQUEEgZm9y
IE9wZW5PZmZpY2Uub3JnIFNjcmliYmxlcnOItgQTAQIAIAUCSXanRwIbAwYLCQgHAwIEFQII
AwQWAgMBAh4BAheAAAoJEGDREhckfRz/4QoEAOJ429PsO5oi1xsnX/lraHACYpHNvk4KVghu
cY2p6J8M0WTTlfls96jRYGlDBDuyZcfW0W+VJlaiu28u2Y9zEnXTWHMlIk6PiOmLPxXofgDf
lKRqvBFYdRD8+33TBeD6u6qajNOLYTL08dnqCfVqmJTGZxqXTmYIOF1NdIs0KlF/
=1y5I
-----END PGP PUBLIC KEY BLOCK-----
```
Then you add the key with:
```
sudo apt-key add office.key
```
After that you'll need to update your aptitude with:
```
sudo apt-get update
```
And finally you can upgrade with:
```
sudo apt-get upgrade
```

Yes, there are other methods but I think this is the safest (and easiest) way to do it.

Good luck.

---

### Post by jamaas on 2009-07-08
Thanks darolu

So far so good, seems to work!

Regards

J

---

