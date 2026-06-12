---
title: "Why partner security, backports and proposed repositories are always empty?"
date: 2010-05-24
forum: General Help
---

### Post by mgol on 2010-05-24
I've noticed that for every Ubuntu release (let's name it codename) all partner apps are located in codename; repositories codename-updates, codename-security and codename-backports are always empty. I've seen a few Skype updates recently and all of them went to codename, not codename-updates (like in main Ubuntu repos).

The question is - why do they even exist then?

---

### Post by -humanaut- on 2010-05-25
My Partner, Backports and proposed updates aren't empty? Are you sure yours are enabled?

---

### Post by mgol on 2010-05-25
> **-humanaut- said:**
> My Partner, Backports and proposed updates aren't empty? Are you sure yours are enabled?

They are. I'm talking about partner repositories, not main/restricted/universe/multiverse.

You cannot compare words "partner" and "-backports" as they refer to different things. You can compare e.g. "partner" with "universe" or "-backports" with "-updates", etc.

Example for Lucid (entries in /etc/apt/sources.list and corresponding Packages file on servers):
[deb http://archive.canonical.com/ubuntu lucid partner](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages)
[deb http://archive.canonical.com/ubuntu lucid-security partner](http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/binary-amd64/Packages)
[deb http://archive.canonical.com/ubuntu lucid-updates partner](http://archive.canonical.com/ubuntu/dists/lucid-security/partner/binary-amd64/Packages)
[deb http://archive.canonical.com/ubuntu lucid-proposed partner](http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/binary-amd64/Packages)
[deb http://archive.canonical.com/ubuntu lucid-backports partner](http://archive.canonical.com/ubuntu/dists/lucid-backports/partner/binary-amd64/Packages)

Only the first file is not empty. You can check it's the same with Karmic, Hardy etc.

---

### Post by -humanaut- on 2010-05-25
Yeah, your right I miss read it. I didn't know you where talking strictly about the 'partner' repos.

---

