---
title: "Adding Mint Repos to Ubuntu"
date: 2012-07-25
forum: General Help
---

### Post by BrokenKingpin on 2012-07-25
How would I go about adding the Mint repos to Ubuntu?

---

### Post by wheeze on 2012-07-25
You need to add the appropriate line to your /etc/apt/sources.list file. Each Mint release corresponds to a particular Ubuntu release, so pick the Mint version that matches your Ubuntu version and add a line like this to the file mentioned:

```
deb http://packages.linuxmint.com/ maya main upstream import backport romeo universe multiverse
```

This would give you all the Mint repos for Mint 13 (Maya) which corresponds to Ubuntu 12.04.

To be complete you should also create a file called **preferences** in the /etc/apt/ directory with the following contents:

```
Package: *
Pin: release o=linuxmint
Pin-Priority: 700

Package: *
Pin: origin packages.linuxmint.com
Pin-Priority: 700

Package: *
Pin: release o=Ubuntu
Pin-Priority: 500
```

This lets any Mint-modified files override their Ubuntu counterparts if required.

Do **sudo apt-get update** after these changes.

---

### Post by wheeze on 2012-07-25
Oops, forgot...

When you do the apt update you'll get an error about a missing keyring file. Install **linuxmint-keyring** and update apt again.

---

### Post by BrokenKingpin on 2012-07-25
Where do I install linuxmint-keyring from, the Mint repos? If so  we may have a chicken and egg thing going on here...

EDIT: It would appear the install of the keyring works fine. Thank you very much for the information.

---

### Post by wheeze on 2012-07-25
> **BrokenKingpin said:**
> Where do I install linuxmint-keyring from, the Mint repos? If so  we may have a chicken and egg thing going on here...

Yes, you'll install it from the Mint repos you just added. No chicken/egg, you just get a warning that you're installing an unauthenticated package. Just go ahead and install it, update again and you'll get no further errors.

---

### Post by BrokenKingpin on 2012-07-25
> **wheeze said:**
> Yes, you'll install it from the Mint repos you just added. No chicken/egg, you just get a warning that you're installing an unauthenticated package. Just go ahead and install it, update again and you'll get no further errors.
Awesome... thanks again.

*Marked as solved.

---

### Post by wheeze on 2012-07-25
No problem :)

I often do this build custom Mint installations starting from an Ubuntu mini.iso.

---

### Post by BrokenKingpin on 2012-07-25
> **wheeze said:**
> No problem :)

I often do this build custom Mint installations starting from an Ubuntu mini.iso.
Exactly what I am doing :).

---

