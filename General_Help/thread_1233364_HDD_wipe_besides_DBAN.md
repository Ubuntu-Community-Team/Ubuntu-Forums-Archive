---
title: "HDD wipe besides DBAN?"
date: 2009-08-06
forum: General Help
---

### Post by cptrohn on 2009-08-06
Hi I am trying to wipe a HDD and DBAN isn't working for me at the moment... it gives me a bad sectors error and won't run...  This HDD is actually very new and there is no way it has bad sectors already

---

### Post by cptrohn on 2009-08-06
Gparted live cd maybe?

Got it downloading now... hope it works

---

### Post by starcraft.man on 2009-08-06
> **cptrohn said:**
> Gparted live cd maybe?

Got it downloading now... hope it works

Not the same thing, gparted would simply delte the partition table. That can be undone and data recovered. It won't securely erase. Gparted is available from the live Ubuntu CD btw, no need to get the gparted live disc.

If ya ask me, it must be a bad burn of DBAN, re download and check md5 hash against file and burn. DBAN works pretty flawlessly in my experience.

I did come across this: [Shred.]("http://en.wikipedia.org/wiki/Shred_%28Unix%29") It is part of GNU core utils, so on all linux machines. Can simply be used from an Ubuntu live CD by command line. Please see man page for it :

```
man shred
```

Warning! If your unsure how to use it or dban, ensure you remove all other drives you don't want wiped so there's no possibility of mess up.

---

### Post by del_diablo on 2009-08-06
What about old dd to get the job done?

---

### Post by cptrohn on 2009-08-06
> **starcraft.man said:**
> Not the same thing, gparted would simply delte the partition table. That can be undone and data recovered. It won't securely erase. Gparted is available from the live Ubuntu CD btw, no need to get the gparted live disc.

If ya ask me, it must be a bad burn of DBAN, re download and check md5 hash against file and burn. DBAN works pretty flawlessly in my experience.

I did come across this: [Shred.]("http://en.wikipedia.org/wiki/Shred_%28Unix%29") It is part of GNU core utils, so on all linux machines. Can simply be used from an Ubuntu live CD by command line. Please see man page for it :

```
man shred
```

Warning! If your unsure how to use it or dban, ensure you remove all other drives you don't want wiped so there's no possibility of mess up.

I'll give it a try!  Thanks.

---

### Post by cptrohn on 2009-08-06
> **del_diablo said:**
> What about old dd to get the job done?

What is old DD?

---

### Post by starcraft.man on 2009-08-06
> **cptrohn said:**
> What is old DD?

dd is a legacy UNIX program that is still about. It's a low level copy and conversion program, it isn't standard like other GNU utils which can be irritating. If your unsure, I'd recommend sticking to DBAN, and if new burn fails a live CD with shred.

[dd]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

---

### Post by dcstar on 2009-08-07
> **starcraft.man said:**
> dd is a legacy UNIX program that is still about. It's a low level copy and conversion program, it isn't standard like other GNU utils which can be irritating. If your unsure, I'd recommend sticking to DBAN, and if new burn fails a live CD with shred.

[dd]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

dd is just as effective at "wiping" modern hard drives as DBAN (or any multi-wipe tool).

All modern ATA standard drives have built-in Secure Wipe functions, you can find free tools (like the NIST one) that can access this function.

---

### Post by egalvan on 2009-08-07
> **cptrohn said:**
> This HDD is **actually very new ****and there is no way it has bad sectors already**

Being new is NO guarantee against being defective.

Electronics can be dead out-of-the-box (DOA),
or die within a very short time (Infant Mortality)

It's what Manufacturer's Warranty is made to cover. :)

Or DBAN may not like that drive.

---

### Post by mahdif62 on 2010-05-14
Use this code:
```
shred -vfz -n 100 /dev/hda
```

---

