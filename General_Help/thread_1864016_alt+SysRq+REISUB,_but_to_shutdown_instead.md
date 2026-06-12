---
title: "alt+SysRq+REISUB, but to shutdown instead?"
date: 2011-10-18
forum: General Help
---

### Post by teejay17 on 2011-10-18
Hi all,
Sometimes my system freezes on shutdown. Rather than have to reboot it with alt+SysRq+REISUB and wait for the machine to fully reboot in order just to power it off, is there an alternative alt+SysRq command to force the machine to power off when it is frozen?

---

### Post by decoherence on 2011-10-18
in theory it should be

alt+SysRq+REISUO

i'm not really sure where the SysRq key is on this here laptop so i haven't tested

---

### Post by teejay17 on 2011-10-18
> **decoherence said:**
> in theory it should be

alt+SysRq+REISUO

i'm not really sure where the SysRq key is on this here laptop so i haven't tested
Well, it sort of worked: I tried the command and it effectively turned off my hard drive. My fans and monitor remained on, however, but I guess if the drive is already off a hard shut down won't hurt anything.

---

### Post by decoherence on 2011-10-20
> **teejay17 said:**
> Well, it sort of worked: I tried the command and it effectively turned off my hard drive. My fans and monitor remained on, however, but I guess if the drive is already off a hard shut down won't hurt anything.

True dat. I guess it halts the machine but doesn't sent an acpi shutdown.

---

### Post by philinux on 2011-10-20
> **decoherence said:**
> True dat. I guess it halts the machine but doesn't sent an acpi shutdown.

It does on my desktop. Not tried it on the lappy.

---

### Post by teejay17 on 2011-10-20
Well I tried it again on my desktop, and this time it shut everything down. 
It also works no problem on my two laptops with Ubuntu installed, so there must be something wonky with the aspi on my desktop.

---

