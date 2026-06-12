---
title: "Slow startup from USB HDD"
date: 2010-06-11
forum: General Help
---

### Post by cipher_lx on 2010-06-11
Hi,

I've installed Ubuntu 10.04 on external HDD. Everything works fine except for slow startup.

It takes at least 2-3 mins to first show a blinking cursor when booting from USB HDD to start ubuntu. After that it starts up within a minute or two?

Any suggestions on what can be done to speed up to boot to Ubuntu from USB HDD?

---

### Post by chayzer on 2010-06-11
Is this before or after the GRUB menu?

If it's after you can edit out the "quiet" in your kernel line and boot that for a more verbose boot. That might give you a clue.

---

### Post by cipher_lx on 2010-06-12
This happens before the GRUB menu!

---

### Post by chayzer on 2010-06-12
Yikes!

Any BIOS updates availabe for your motherboard?

Maybe play with the boot order or some other options in your BIOS settings too to try and narrow it down.

---

### Post by chayzer on 2010-06-12
Carefully, I might add.

---

### Post by garvinrick4 on 2010-06-12
Boot order should always be CD first then USB then HDD. Then leave it be.

---

### Post by cipher_lx on 2010-06-13
Not sure if bios update is available for my motherboard. The current version that I have is Phenoix F.33.

My current boot order is USB HDD, CD-ROM, Internal HDD...

---

### Post by garvinrick4 on 2010-06-13
> **cipher_lx said:**
> Not sure if bios update is available for my motherboard. The current version that I have is Phenoix F.33.

My current boot order is USB HDD, CD-ROM, Internal HDD...
A CD is always going to be the Live medium that you have to fix a machine. Making it be the
first to boot hurts nothing and has everything to gain. I know if you unplug your USB devices CD will be the first then but why not just keep it #1.

---

