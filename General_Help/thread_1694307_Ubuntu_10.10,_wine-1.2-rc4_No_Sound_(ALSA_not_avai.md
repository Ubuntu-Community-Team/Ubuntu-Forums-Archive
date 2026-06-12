---
title: "Ubuntu 10.10, wine-1.2-rc4 No Sound (ALSA not available in winecfg)"
date: 2011-02-24
forum: General Help
---

### Post by calris on 2011-02-24
I'm trying to get sound working in wine

When I run winecfg my only options are OSS and NAS both of which give 'Audio test failed!' if I click on the 'Test Sound' button. Numerous posts suggest using ALSA *brrrrr* wrong answer - ALSA is not available in winecfg and trying to hack the registry gives an error in winecfg 'Found driver in registry that is not available'

Virtual Box works fine with ALSA

What gives?

---

### Post by dino99 on 2011-02-24
you should update your system, latest wine is: 1.3.14

[https://launchpad.net/~ubuntu-wine/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~ubuntu-wine/+archive/ppa?field.series_filter=maverick)

---

### Post by Gintautas on 2011-03-04
i have the same problem. I can give a little better description, when i select configure start to manage wine versions, and select exact wine version like 1.3.14 for an application i receive the very same error as an author, in audio graph of configure wine i see only oss driver available, and when i click on test sound it gives me a fail. Also a message pop ups saying: "Found driver in registry that is not available, remove alsa from registry?". If i chose wine version to system, then i am able to chose various sound drivers and all of them seem to work, still some games do not run on "system wine version" settings, so i have to chose play with no sound or do not play at all.

---

