---
title: "trim ubuntu for netbook"
date: 2011-11-06
forum: General Help
---

### Post by techvish81 on 2011-11-06
i want to trim down ubuntu to use it on a netbook where the use of a lot of system apps is not required, actually i want to remove, ubuntuone,firefox,thunderbird,gwibber, empathy, (all chat stuff), banshee, brasero etc.. 

can i remove them safely without causing instability? 
i also want to remain able to update via update-manager.

plz give proper guidance..

and yes, i dont want to use lubuntu, xubuntu and so on...

---

### Post by pqwoerituytrueiwoq on 2011-11-06
have you tried the netbook version?
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
search for "Netbook live CD" there

---

### Post by techvish81 on 2011-11-06
> **pqwoerituytrueiwoq said:**
> have you tried the netbook version?
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
search for "Netbook live CD" there

i want to use 11.10 oneiric, so plz tell me how can i trim it down by removing unwanted apps.
thanks for reply

---

### Post by waloshin on 2011-11-06
The normal version of Ubuntu runs fine on a netbook otherwise there is Ubuntu netbook edition.

---

### Post by mike555 on 2011-11-06
This is what I used to remove;

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

---

### Post by WorMzy on 2011-11-06
If you want a minimal operating system, you're using the wrong distro.

I recommend that you install Arch, which gives you a barebones system. From there you can install just what you need. Depending on what DE and "extras" you install, you can usually build a usable system that uses >2GB.

---

### Post by techvish81 on 2011-11-06
> **mike555 said:**
> This is what I used to remove;

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.



thank you very much, it worked, my netbook has become pretty much snappy now.

---

### Post by techvish81 on 2011-11-06
one more thing , remove compiz and compiz core only if you want to remove unity (3d) login option, i use ubuntu 2d so i had no problems at all, it has really become much responsive.

---

### Post by pretty_whistle on 2011-11-06
> **mike555 said:**
> This is what I used to remove;

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.
Thanks.  That helped me too! :D

---

### Post by techvish81 on 2011-11-07
arch is for people who are very much comfortable with the terminal,  I've tried it but it is like do-it-yourself OS

---

