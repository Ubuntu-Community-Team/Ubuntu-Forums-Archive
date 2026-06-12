---
title: "Building Seamonkey"
date: 2010-01-14
forum: General Help
---

### Post by Bumbler on 2010-01-14
What do I need to know about patches in order to build the latest Seamonkey on Ubuntu 9.10 64-bit?

It is hardly a complaint for me to notice the developers are too busy to worry about Seamonkey. It's lagging current release significantly, and I am inclined to build the latest for myself. I already know about the commands like "build-dep" and so forth, so the issue here is something more specific.

What sort of patching is done by the Ubuntu developers for building Seamonkey? Would it fail to build if I simply followed the generic path? Downloading the community builds is not an option for 64-bit, since they are built on the oldest generic libs available -- libc5, gtk1, etc.

---

### Post by gradinaruvasile on 2010-01-14
Have you tried the generic build on their site? Maybe it works with 64-bit...

[http://download.mozilla.org/?product=seamonkey-2.0.2&os=linux&lang=en-US](http://download.mozilla.org/?product=seamonkey-2.0.2&os=linux&lang=en-US)

---

### Post by Bumbler on 2010-01-14
Tried it, thank you. The generic scripts do not cooperate with 64-bit, nor have they ever done so for as long as I can remember.

---

### Post by gradinaruvasile on 2010-01-14
Tried linux32 ? Like (not sure exactly how or if it works, i have 32 bit system):

linux32 seamonkey

linux32 should run programs in 32 bit compatibility mode.

---

### Post by Bumbler on 2010-01-14
No, because I'm really not interested in playing with 32-bit. I appreciate your efforts, my friend ( :D ), but this isn't a plea for help getting Seamonkey *running*, but *built*. I am really much more interested in learning how to struggling with building 64-bit stuff.

**Update:** Okay, maybe not necessary this round. Someone has stepped up to the plate.

> deb [http://ppa.launchpad.net/joe-nationnet/ppa-seamonkey2/ubuntu](http://ppa.launchpad.net/joe-nationnet/ppa-seamonkey2/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/joe-nationnet/ppa-seamonkey2/ubuntu](http://ppa.launchpad.net/joe-nationnet/ppa-seamonkey2/ubuntu) karmic main
key A8F0C7B7

---

