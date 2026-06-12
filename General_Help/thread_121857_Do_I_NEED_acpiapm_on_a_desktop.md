---
title: "Do I NEED acpi/apm on a desktop?"
date: 2006-01-26
forum: General Help
---

### Post by el3ktro on 2006-01-26
Hi,
I have an Athlon64/nForce4 system, but running 32bit Ubuntu. One thing I really want is that the CPU lowers its speed when it's not in use, and powernowd does that fine. But I'm wondering, do I really need the ACPI & APM stuff that is loading during boot? On my previous Gentoo system, I never had those, and I can't see any difference with my current system. The same goes for hotplug ... I never had it installed on my previous system, but still hotplugging USB sticks, cameras etc. worked fine. So, on my desktop system (no suspend/hibernate) do I really need them? Could I savely uninstall them & ave boot time + resources?

Tom

---

### Post by epostma on 2006-01-26
For APM & ACPI, the answer is that if you don't want their features, you can remove them. But I wouldn't recommend removing hotplug. It's used for some very clever jiggery-pokery at startup (might be replaced by [coldplug]("http://www.google.com/url?sa=t&ct=res&cd=4&url=http%3A//lists.debian.org/debian-devel/2005/08/msg01247.html&ei=rNzYQ9TuCaHQQv2KvOcD&sig2=_eGAdYkoBDwALxUgnijlsg") sometime).

---

### Post by el3ktro on 2006-01-26
So what exactly are the features of ACPI/APM? As long as it comes to CPU freq scaling, I can tell from Gentoo that it also works w/o ACPI/APM as init scripts - and beyond that, I'm doing nothing like hd spindown, hibernation/suspension etc.

Tom

---

### Post by az on 2006-01-26
I think both apm and acpi are both a kernel option or module as well as a userspace tool.  Whether you recompile your kernel to omit the acpi and apm options is up to you.  I am pretty that frequency scaling is an acpi kernel thing.

As for the userspace tools, you can remove the power management and apm packages (look for powermgmt-base, and acpi package and the apmd package)  I doubt that you will see any noticeable reduction in boot time or memory useage, though.

---

### Post by el3ktro on 2006-01-26
Well I just want to remove everything I don't really need :-) This reduces bugs, updates, resource consumption ... ;-)

Tom

---

### Post by az on 2006-01-26
[QUOTE=el3ktro]Well I just want to remove everything I don't really need :-) This reduces bugs, updates, resource consumption ... ;-)

Tom[/QUOTE]

If you remove some of those packages, you will end up removing the ubuntu-desktop package and may not be able to dist-upgrade smoothly without re-installing it.

ubuntu-desktop is the metapackage that will bring in every opther package and feature that a new release will have.

It is just more convenient to keep it around, in many cases.

---

### Post by el3ktro on 2006-01-26
Hmm well I actually removed a LOT of apps that are in ubuntu-desktop, like Evolution, Gnome games, everthing Bluetooth-related, some parts of OOo, the screensavers, some fonts etc. I never heart that problems could arise by removing such a meta-package. I try to remove nothing which is in ubuntu-minimal though.

Tom

---

