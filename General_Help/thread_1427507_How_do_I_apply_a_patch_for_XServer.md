---
title: "How do I apply a patch for XServer?"
date: 2010-03-11
forum: General Help
---

### Post by Remagen on 2010-03-11
Heyo,

I have compiz fusion and an ATI card (FGLRX driver) installed.  This means that my windows are painfully slow to resize/min/max.  This has bugged me for awhile, but apparently someone found a fix, as specified in:
 107_fedora_dont_backfill_bg_none.patch

[Basically, they commented out most of a function].

My question is how do I apply this patch?  It causes problems for people using KDE on intel cards, but that won't bother me since I'm AMD on gnome.

---

### Post by Compyx on 2010-03-11
To apply that patch you'll need to download the source of XServer and apply the patch via the 'patch' command. Then you'll have to recompile the XServer and install it (probably along with some other X11-related packages). All this means overwriting the XServer package provided by Ubuntu with your own compiled version. To keep that version you'll have to 'pin' the XServer package provided by Ubuntu to avoid having an update overwrite your patched XServer binary.

My advice would be to stick to the packages provided through Ubuntu and see if there's a bug filed on Launchpad, maybe someone is already working on a patch.
Mixing your own compiled stuff with stuff provided through a package manager can be tricky and should only be done if you really know what you're doing.

---

