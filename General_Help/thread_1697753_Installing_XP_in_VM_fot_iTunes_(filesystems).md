---
title: "Installing XP in VM fot iTunes (filesystems)"
date: 2011-03-01
forum: General Help
---

### Post by nothingspecial on 2011-03-01
My Dad just bought my son a brand new ipod touch.

I have an XP disk somewhere. I'll install it in a VM.

Will I have to format my external drive to something other than ext3 in order for the virtual windows' itunes to read it or will (please, please please), because it is virtual and running inside linux, it be able to use it?

Thanks

---

### Post by HereInOz on 2011-03-01
When you connect a USB drive to a virtualised XP machine, it is as if the drive is directly plugged into the XP machine, so if it is formatted as ext3, XP won't have a clue about it.

I see a reformat looming in your future.

---

### Post by nothingspecial on 2011-03-01
Oh poo

anyway, I have a plan B, An 8 gig stick will hold my son's music. That can be his itunes library for now.

cheers

(I recognize that dog)

---

### Post by franchoy on 2011-03-01
When you run Itunes on virtualbox it crashes. Just install it under Wine...

---

### Post by nothingspecial on 2011-03-01
> **franchoy said:**
> When you run Itunes on virtualbox it crashes. Just install it under Wine...

ok, I'll try

---

### Post by Mark Phelps on 2011-03-01
Wine is very much a hit-or-miss proposition.

See the link to the WineHq page below for iTunes:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

The recent versions are rated Garbage (won't work at all) or Bronze (will barely work).

---

