---
title: "Installed proprietary drivers (radeon HD 4670), now will not dual screen"
date: 2012-06-30
forum: General Help
---

### Post by tippx1 on 2012-06-30
Setup info:
(This is on a desktop. It does say laptop in the screenshots for some reason)
OS: Ubuntu 12.04

Right monitor: DVI 20 inch HP 1600x900 monitor (In displays as Laptop), Left: VGA Insignia 1366x768 TV (in displays as XH@22")

Video Card: HIS Radeon HD 4670

[[COLOR="Blue"]Screenshots album[/COLOR]]("http://imgur.com/a/Vqw6e")
First screenshot is default settings. It shouldnt matter, but I forgot to switch the locations of the monitors before this screenshot was taken
Second, I am trying to not mirror, but extend the two monitors 
Third and fourth are the error messages I get.

Is here a way to fix this, or should I go back to the open drivers?

---

### Post by tippx1 on 2012-06-30
Just googled a little more after submitting this and solved it.

Anyone who is here from google/forum search with the same issue:

[Solved it here]("http://askubuntu.com/questions/126392/problem-connecting-multiple-monitors-on-12-04-problema-al-conectar-monitores-ub")

> $: gksudo amdcccle

Display Manager> Choose multi-display dekstop with display(s) from the combobox and restart the computer it will fix. You still can't use the real monitor settings.

Searchable text of the error messages:
the position or size required for the CRTC 148 is outside the allowable limits: position = (1366, 0), size = (1366, 768 ), maximum = (1600, 1600)

GDBus.Error: org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: the > position or size required for the CRTC 148 is outside the allowable limits: position = > (1366, 0), size = (1366, 768 ), maximum = (1600, 1600)


I'm not sure what is meant by "You still can't use the real monitor settings", it works fine for me now

---

