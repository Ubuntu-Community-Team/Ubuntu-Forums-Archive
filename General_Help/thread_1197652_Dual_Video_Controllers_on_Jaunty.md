---
title: "Dual Video Controllers on Jaunty"
date: 2009-06-26
forum: General Help
---

### Post by b@sh_n3rd on 2009-06-26
Hi, I've installed a [COLOR=SeaGreen]Matrox MGA 1064SG[/COLOR] on my computer running Jaunty. I wanna use this card with a secondary monitor. How do I do this on Ubuntu? I've done it before on windows though. Thanks for any replies. BTW, it's a PCI card and my primary adapter is an [COLOR=SeaGreen]ATI 3D Rage Pro AGP 1x/2x[/COLOR]. The adapter's in the output of "# lspci | less" I've provided below.```
00:0d.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
```Once again, thanks for any help.

---

### Post by Rob_H on 2009-06-26
Don't have an answer for you, but just curious: Why did you install a second video card instead of using the second output on your existing card (or upgrading it if it doesn't have one)?

---

### Post by b@sh_n3rd on 2009-06-26
> **Rob_H said:**
> Don't have an answer for you, but just curious: Why did you install a second video card instead of using the second output on your existing card (or upgrading it if it doesn't have one)?

maan you gave me false hopes. Me ATI is an old card and me PC is also old. It's just got a single VGA Port :D.

---

### Post by b@sh_n3rd on 2009-06-27
Anyone? I take it I need to edit my xorg.conf for an extra device, an additional monitor and a secondary screen? I tried it first but it didn't seem to work...

---

### Post by fugitivo82 on 2009-07-08
b@sh_n3rd, do you can fix your problem? I have the same problem :cry:

---

### Post by b@sh_n3rd on 2009-07-08
> **fugitivo82 said:**
> b@sh_n3rd, do you can fix your problem? I have the same problem :cry:

Hi **fugitivo82**. Nope. All I could figure out was that I need secondary entries in my xorg.conf file for the second video adapter. For that I need to set the BusId...now I know what the BusId for my second card *is* but it's weird...I'm not sure how it should be entered into my xorg.conf file. As I'd mentioned in a previous post the BusId for the Matrox is, "00:0d". My primary adapter, the ATI 3D Rage Pro is, "01:00". This I know should be entered like, 'BusId <tab> "PCI:1:0:0" '. Now the other one I'm clueless about. Even if I get this right, I don't know if it'll work...

---

