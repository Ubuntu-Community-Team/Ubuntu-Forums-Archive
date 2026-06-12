---
title: "Swap not being used."
date: 2006-04-14
forum: General Help
---

### Post by PriceChild on 2006-04-14
Hi, i'm running Ubuntu Breezy on a:

Home brew
AMD Athlon XP 3000+
768Mb RAM
1Gb Swap

However, running a system monitor tray on my panel, i can see that no matter what i start up, my swap is never used.

This isn't normal is it?

---

### Post by aysiu on 2006-04-14
Actually, with 1 GB of RAM, you'll probably never use swap. This is normal.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=PriceChild]Hi, i'm running Ubuntu Breezy on a:

Home brew
AMD Athlon XP 3000+
768Mb RAM
1Gb Swap

However, running a system monitor tray on my panel, i can see that no matter what i start up, my swap is never used.

This isn't normal is it?[/QUOTE]
Ram is much faster then swap so Ubuntu tried to use all avaible ram to make your system much faster. I have 512 of ram and I'm using no swap and I'm using firefox, listening to music, and I have alot of cool visual things on my computer.

---

### Post by PriceChild on 2006-04-14
[quote=aysiu]Actually, with 1 GB of RAM, you'll probably never use swap. This is normal.[/quote] 
768 Mb ;)

Anyway good good! I just remember seeing reccomendations about always using swap unless you have at least 1Gb of RAM, so better safe than sorry and posted :)

Thanks,
          Pricey

P.s. thanks for the kernel How-to btw masterchief, oh and i'll play you at halo2 on live anyday ;)

---

### Post by dcstar on 2006-04-15
[QUOTE=PriceChild]768 Mb ;)

Anyway good good! I just remember seeing reccomendations about always using swap unless you have at least 1Gb of RAM, so better safe than sorry and posted :)
[/QUOTE]
```
sudo swapon -s
```
will tell you if swap is enabled on your system:
```
sudo swapon -a
```
will turn it on if not.

---

### Post by akiro.yamamoto on 2006-04-16
I have a 768MB on my system. When running firefox , g / xmms , gwget , document viewer (pdf) and apollon my system only uses 180MB of ram and 0 bytes of SWAP.
Which is good since SWAP is much slower than main memory. SWAP is really only useful if you have low mem or your using large data chunks or heavy mem utilization. SWAP is for when the system needs more mem than is installed on your system.

---

### Post by Sirin on 2006-04-16
[QUOTE=PriceChild]Hi, i'm running Ubuntu Breezy on a:

Home brew
AMD Athlon XP 3000+
768Mb RAM
1Gb Swap

However, running a system monitor tray on my panel, i can see that no matter what i start up, my swap is never used.

This isn't normal is it?[/QUOTE]

You have a gig of ram :p and swap is mainly used when you run out of ram.

Your Swap is a piece of hard drive used as RAM, hard drives are slower than RAM, so you don't want any Swap being used at all if possible, though you still need it there just in case

---

