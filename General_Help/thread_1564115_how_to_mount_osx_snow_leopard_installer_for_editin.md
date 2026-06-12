---
title: "how to mount osx snow leopard installer for editing?"
date: 2010-08-30
forum: General Help
---

### Post by kyconny on 2010-08-30
:confused: right I have a dmg of snow leopard 10.6.0.

Using a java applet I have managed to convert that dmg into a iso format.

Although after mounting the iso disk image there is only 1 folder entitled "windows support".

By a quick guess I think I can safely say this is a multisession dvd but how in the world do you mount them?

I need to edit the dvd for the errrrr errrrrrrrrr wallpaper being replaced (chuckles: they dont know anything about the osx86 :o )

anyway I would appreciate your help and I would normaly post at insanely mac but no one has ever done this sort of thing before. ( except on a fully functional leopard install )

TY

---

### Post by kyconny on 2010-08-30
:KS:KS:KS:KS:KS

ALMOST SOLVED :)

Looking at [THIS]("http://www.64lines.com/mounting-hfs-plus") webpage im using hexdump and grep together now to find 48 2b 00 04 then subtracting what all hfs+ partitions start with 1024 or 0x400 from the value of the hex line found with 48 2b 00 04

using that as loop and hopefully mounting the snow leopard install dvd :P

Yes i know its mad but if some person says it on the internet it must work :)

---

### Post by kyconny on 2010-08-30
solved :KS:KS:KS:KS thank you 64lines.com :)

---

### Post by cariboo on 2010-08-30
It is against Apples EULA to install OSX on non-Apple branded hardware. We don't support this type of activity. Thread closed.

---

