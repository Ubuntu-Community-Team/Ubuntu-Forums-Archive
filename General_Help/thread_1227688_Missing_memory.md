---
title: "Missing memory?"
date: 2009-07-30
forum: General Help
---

### Post by Krupski on 2009-07-30
Hi all,

I'm running Ubuntu Server 64 bit on an Intel DQ45CB motherboard with 8 GB of ram installed.

However, only about 7 GB shows up:

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:      [COLOR="Red"]**6981124**[/COLOR]     441140    6539984          0        608     358608
Low:      [COLOR="Red"]**6981124**[/COLOR]     441140    6539984
High:            0          0          0
Swap:      4194296          0    4194296
Total:    11175420     441140   10734280

```

With a different motherboard (Intel DG33BU), the full 8 gigs show up.

Any ideas?

Thanks!

-- Roger

---

### Post by QIII on 2009-07-30
Do you have a dedicated or an integrated graphics card?

Scratch that.  I see "server" now.  Dang bifocals!

---

### Post by fragos on 2009-07-31
Perhaps on that mobo some memory is designated for a different purpose. Simplest example being a mobo with integrated video. If memory is used for a different purpose it is probably configurable in the BIOS setup.

---

### Post by Krupski on 2009-07-31
> **fragos said:**
> Perhaps on that mobo some memory is designated for a different purpose. Simplest example being a mobo with integrated video. If memory is used for a different purpose it is probably configurable in the BIOS setup.

The motherboard has "DVMT" (Dynamic Video Memory Technology) but I have no video card plugged in. I also have no monitor plugged in. In the BIOS setup, there are choices for "128 MB", "256 MB" and "Maximum DVMT" (whatever that means).

However, there seems to be no way to set it to zero.

I just thought of something... I have the bios set to "auto" (for video). Maybe if I set it to "External PCI-E Video" it will release it's internal DVMT memory... ?

I'll try it and report what happens.

---

### Post by fragos on 2009-07-31
Setting it to "External PCI-E Video" sounds like a good idea to me.

---

### Post by Krupski on 2009-07-31
> **fragos said:**
> Setting it to "External PCI-E Video" sounds like a good idea to me.

Well, I tried it. No difference.   :(

---

### Post by Krupski on 2009-07-31
> **fragos said:**
> Setting it to "External PCI-E Video" sounds like a good idea to me.

Well, I found something... and it's really strange. I had the memory timings set to "manual" and selected 6-6-6-18 (which is what the SPD says). I had manual mode because I wanted to set the ram voltage from 1.80 to 2.00 volts.

I switched it to "automatic" and the rest of my ram came back!!!

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:      [COLOR="Red"]**7972348**[/COLOR]     118688    7853660          0        592      54876
Low:      [COLOR="Red"]**7972348**[/COLOR]     118688    7853660
High:            0          0          0
Swap:      4194296          0    4194296
Total:    12166644     118688   12047956

```

The difference is 7972348 - 6981124 = 991224... almost an entire gigabyte!

So I wondered if it was the higher voltage on the ram causing the problem... so I set manual 6-6-6-18, 1.80 volts (exactly what the SPD calls for and supposedly what the MOBO sets the ram to in "automatic" mode).... no difference.

With the board in manual mode, almost a gigabyte of ram evaporates. In auto mode, it's all there.

WHY this happens? I have no idea. VERY strange.

---

