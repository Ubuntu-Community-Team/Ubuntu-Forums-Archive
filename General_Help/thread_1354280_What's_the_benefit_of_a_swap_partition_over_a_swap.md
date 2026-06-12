---
title: "What's the benefit of a swap partition over a swap file?"
date: 2009-12-13
forum: General Help
---

### Post by Vostrocity on 2009-12-13
"The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system."[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
Is there any benefit to this, or is there plan to enable Ubuntu to use a swap file?

---

### Post by Bachstelze on 2009-12-13
The benefit is that you can use hibernation with a swap partition, and you can't with a swap file. If you don't use hibernation, there is none.

---

### Post by audiomick on 2009-12-13
I would consider a swap file to be a kind of help measure if there had not been a swap partition created during installation, or a way of increasing the swap space without re-partitioning, but that is only a guess.

Your question isn't quite clear.
If you mean can Ubuntu use a swap file at all, yes it can.
If you mean is there a plan to allow the use of a swap file for hibernation, I don't know, but I can imagine that that might be difficult. It seems to me that that would mean putting information needed to wake up the system in the sleeping system, a bit like locking your keys in the car.

---

### Post by howefield on 2009-12-14
> **Vostrocity said:**
> ...or is there plan to enable Ubuntu to use a swap file?

I read somewhere that Lucid Lynx will use a swap file instead of a swap partition, but can't find the link any more.

---

### Post by Vostrocity on 2009-12-15
> **Bachstelze said:**
> The benefit is that you can use hibernation with a swap partition, and you can't with a swap file. If you don't use hibernation, there is none.
I know that Windows doesn't use a swap partition, yet can still do hibernation. Not sure about OS X but am curious to know.

> **audiomick said:**
> Your question isn't quite clear.
If you mean can Ubuntu use a swap file at all, yes it can.
If you mean is there a plan to allow the use of a swap file for hibernation, I don't know, but I can imagine that that might be difficult. It seems to me that that would mean putting information needed to wake up the system in the sleeping system, a bit like locking your keys in the car.
Sorry I realize that now that I reread my first post. Personally I have enough to RAM to not need swap space. However I still want to use hibernate. That's why I'm reluctant to dedicate another partition just for the occasional hibernation.

> **howefield said:**
> I read somewhere that Lucid Lynx will use a swap file instead of a swap partition, but can't find the link any more.
Sure hope so.

---

