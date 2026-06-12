---
title: "VBox wants x86-64 PCU"
date: 2011-06-01
forum: General Help
---

### Post by layers on 2011-06-01
I am trying to install this particular Debian-based distro in VirtualBox, but upon trying to install it, I get the massage
```
This kernel requires an x86-64 CPU, but only detected an i646 CPU.
```

The host system is 64 Natty, with i5-M460. What am I missing? I thought everything is 64 bit in front of me...

---

### Post by plucky on 2011-06-01
> **layers said:**
> I am trying to install this particular Debian-based distro in VirtualBox, but upon trying to install it, I get the massage
```
This kernel requires an x86-64 CPU, but only detected an i646 CPU.
```

The host system is 64 Natty, with i5-M460. What am I missing? I thought everything is 64 bit in front of me...

Did you install virtualbox from Ubuntu Software Centre or Synaptic Package Manager?

Or 

Did you download the X86-64 version from Oracle Website?

If from the former,it is probably an X86 application.

Good Luck

---

### Post by 3rdalbum on 2011-06-01
> **layers said:**
> I am trying to install this particular Debian-based distro in VirtualBox, but upon trying to install it, I get the massage
```
This kernel requires an x86-64 CPU, but only detected an i646 CPU.
```

The host system is 64 Natty, with i5-M460. What am I missing? I thought everything is 64 bit in front of me...

Does the i5 support virtualisation extensions? You need to make sure these are active in Virtualbox's settings in order to run a 64-bit guest OS. The tooltips for the Vbox settings will tell you which one allows you to run 64-bit guests.

---

### Post by layers on 2011-06-01
> **plucky said:**
> Did you install virtualbox from Ubuntu Software Centre or Synaptic Package Manager?

Or 

Did you download the X86-64 version from Oracle Website?

If from the former,it is probably an X86 application.

Good Luck
 
First, I got it from SC, but then remembered that, and went and got the AMD64 version.

---

### Post by layers on 2011-06-01
> **3rdalbum said:**
> Does the i5 support virtualisation extensions? You need to make sure these are active in Virtualbox's settings in order to run a 64-bit guest OS. The tooltips for the Vbox settings will tell you which one allows you to run 64-bit guests.
How do I know that again?

---

### Post by layers on 2011-06-01
ALright, I'll just use 32 bit OS.

---

