---
title: "Why does Ubuntu use such a trailing edge lvm2?"
date: 2012-04-28
forum: General Help
---

### Post by Nutria on 2012-04-28
Hi,

Precise installs lvm2 2.02.66, which is from May 20**[SIZE="2"]10[/SIZE]**.  The version as of Oct-2011 was 2.02.88.  A huge number of features has been added since then, and the lvm2 mailing list naturally doesn't like supporting such an ancient version.

Sincerely,
Ron

---

### Post by xyzzyman on 2012-04-29
Because .66 is the version in debian-stable. You'll have to go upstream to debian if you think that is an issue. I'm suprised the mailing list isn't aware of this.

---

### Post by Nutria on 2012-04-29
> **xyzzyman said:**
> Because .66 is the version in debian-stable.

:confused:  Stable also uses the **[SIZE="2"]Lucid[/SIZE]**-era kernel is 2.6.32 and GNOME 2.30 so *Debian Stable uses it so we should too* doesn't seem valid logic.

---

### Post by xyzzyman on 2012-04-29
> **Nutria said:**
> :confused:  Stable also uses the **[SIZE="2"]Lucid[/SIZE]**-era kernel is 2.6.32 and GNOME 2.30 so *Debian Stable uses it so we should too* doesn't seem valid logic.

You do realize that Ubuntu is a Debian derivative, and most packages are downstream from Debian, right? You could take over package management for lvm2 on Ubuntu if you want to volunteer and merge from Debian unstable and handle any issues that come up. Until then, it'll come from upstream debian-stable.

EDIT: Or contact the current maintainer and offer to take it over: [https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/726677](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/726677)

---

### Post by Nutria on 2012-04-29
*Maintainer is too busy* is a perfectly reasonable justification.  *Must track Stable* is not.

Anyway, I should have thought to look at the bug list first.  :(

---

