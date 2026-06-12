---
title: "Difference between Hoary and Warty live CD`s?"
date: 2005-01-30
forum: General Help
---

### Post by Reppyboyo on 2005-01-30
Ive tried both and only "Hoary" starts up with no problems at all, "Warty" however gives me the "No Screens Found" error using whatever driver (vesa, ati, radeon).

Whats the differance between the two which could cause this?
Does the "Hoary" release contain an updated driver of somesuch?

Would be nice to know so I can finally get the install version.

Thanks anyone.

---

### Post by BWF89 on 2005-01-30
Theres a Hoary live cd? This is news to me.

---

### Post by JoWilly on 2005-01-30
[QUOTE=Reppyboyo]Ive tried both and only "Hoary" starts up with no problems at all, "Warty" however gives me the "No Screens Found" error using whatever driver (vesa, ati, radeon).

Whats the differance between the two which could cause this?
Does the "Hoary" release contain an updated driver of somesuch?

Would be nice to know so I can finally get the install version.

Thanks anyone.[/QUOTE]

Warty uses Xfree86, Hoary uses Xorg.

---

### Post by TekMate on 2005-01-30
Warty was based on another distro, it wasn't really Ubuntu while Hoary is.

---

### Post by JoWilly on 2005-01-30
[QUOTE=BWF89]Theres a Hoary live cd? This is news to me.[/QUOTE]

Yes, and a new Hoary live cd iso comes out about every day (sometimes even twice a day), as I have discovered 2 days ago when I tried ubuntu for the first time :).

Just check the cdimage dir at the root of the ubuntu ftp.

---

### Post by BWF89 on 2005-01-30
[QUOTE=JoWilly]Yes, and a new Hoary live cd iso comes out about every day (sometimes even twice a day), as I have discovered 2 days ago when I tried ubuntu for the first time :).

Just check the cdimage dir at the root of the ubuntu ftp.[/QUOTE]
Talk about bleeding edge.

---

### Post by Reppyboyo on 2005-01-31
So is xorg faster than xfree86 or just more compatable?
Any change xorg will work on Warty, or should I just stick to the Hoary releases?

---

### Post by alastair on 2005-01-31
Xorg is a fork of XFree86. Many dists have moved to X.org servers (e.g. Redhat/Fedora, FreeBSD etc.).  I'd stick with what works for you just now - the next release of Ubuntu will be Xorg.

---

### Post by JoWilly on 2005-01-31
[QUOTE=Reppyboyo]So is xorg faster than xfree86 or just more compatable?
Any change xorg will work on Warty, or should I just stick to the Hoary releases?[/QUOTE]

Hoary works perfectly stable over here. Plus, Hoary has the ati fglrx drivers (you need the xorg-fglrx driver + linux-restricted-modules which contains the kernel module) in the repositories (Warty not).

---

