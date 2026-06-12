---
title: "Update Ruined Flash"
date: 2011-11-12
forum: General Help
---

### Post by PsyclonJohn on 2011-11-12
I just got an update in the update manager for Flash, so I went and updated like usual... next thing I know, my flash is no longer being detected. 

It was saying 'Missing Plugin', so I restarted Chrome, and now it says Update to Flash 10. I don't get it, everything was working great before the update.

---

### Post by PsyclonJohn on 2011-11-12
Just tried to update via Adobe Flash Website and got this:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by PsyclonJohn on 2011-11-12
I just tried accessing Synaptic Package Manager and I've been given this error: 

Package 'adobe-flashplugin' is virtual

For anyone else having this problem, mark the flash plugin for re-installation (took sorta long), but it fixes this bug.

---

### Post by dajare on 2011-11-12
Yep. Me too. :(

> **PsyclonJohn said:**
> I just got an update in the update manager for Flash, so I went and updated like usual...

+

For anyone else having this problem, mark the flash plugin for re-installation (took sorta long), but it fixes this bug.

I couldn't find any "adobe" entries in Synaptic, but (re-?)installing the flashplugin-nonfree-extrasound package fixed it for me.

Disconcerting....

---

### Post by mistacool on 2011-11-12
> **dajare said:**
> Yep. Me too. :(



I couldn't find any "adobe" entries in Synaptic, but (re-?)installing the flashplugin-nonfree-extrasound package fixed it for me.

Disconcerting....

I haven't had any issues with the Flash update but an update from two days ago somehow broke Synaptic on my system. The complete removal option now only removes the single selected file. Maybe it's related?

---

