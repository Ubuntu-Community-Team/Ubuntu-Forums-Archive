---
title: "vbox, ubuntu host, xp guest, ram"
date: 2011-07-13
forum: General Help
---

### Post by nothingspecial on 2011-07-13
I'm using xp in virtual box. The sole purpose of which is to manage my sons' iPod touches in iTunes.

I have 3 gigs of ram. I run Ubuntu on other machines with 1 gig fine.

Am I safe, assuming I'm not compiling gnome 3 or batch converting videos etc, to assign 2 gigs of ram to the virtual machine. And still be able to do some low memory stuff on my Ubuntu host?

I don't know how it works. When you assign 2 gigs of ram, is that to virtual box and the guest, or just to the guest meaning that vbox itself uses ram from the 1 gig left......

.....if you see what I mean.

Thank you.

---

### Post by dino99 on 2011-07-13
allowing 1 giga is much more than needed

---

### Post by seawolf167 on 2011-07-13
> **dino99 said:**
> allowing 1 giga is much more than needed

Agreed - if all you are doing is booting the system to browse for iPod/iTunes items, you are way more than ok with 1 GB Ram

---

### Post by nothingspecial on 2011-07-13
Thanks, it's just with 40,000 odd tunes iTunes runs like a brick through treacle. I thought some extra ram might help.

I suppose the other approach would be to only load what the kids want into it's library.

---

### Post by seawolf167 on 2011-07-13
Its too bad iTunes through Wine is terrible. I know that with Guest Additions installed you can share the hosts physical RAM with many virtual machines (I think its called memory ballooning?). As for RAM allocation through the settings menu for each virtual machine, memory above the memory needed but below the RAM allocation should be returned as free memory to the host until needed by that particular virtual machine.

---

### Post by nothingspecial on 2011-07-13
That's exactly what I wanted to know, cheers.

---

