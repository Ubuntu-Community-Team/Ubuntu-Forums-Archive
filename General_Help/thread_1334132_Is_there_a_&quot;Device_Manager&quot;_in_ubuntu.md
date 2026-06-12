---
title: "Is there a &quot;Device Manager&quot; in ubuntu"
date: 2009-11-22
forum: General Help
---

### Post by emigrant on 2009-11-22
hi all ;)

is there a 'device manager' kind of thing in ubuntu?
which allows me to see what which VGA card i have enabled, and how to disable the onboard VGA card etc...

thank you all.

:popcorn:

---

### Post by warfacegod on 2009-11-22
Yes, there are several. Go to add/remove applications, under system tools you will what you are looking for I believe. Things like Sysinfo or Device Manager. I don't recall if can use them to disable your hardware or not but, at least, it's a start.

---

### Post by coffeecat on 2009-11-22
> **emigrant said:**
> and how to disable the onboard VGA card etc

Disable onboard video in the BIOS. Usually the BIOS should do that for you automatically when you plug in an AGP or PCIe video card, but sometimes you have to do it yourself. And if you do have to do it yourself, be warned. Depending on the BIOS manufacturer, the setting name may not be particularly intuitive. It was quite misleading in my Abit motherboard.

---

### Post by jeb800e on 2009-11-22
System < Preferences < Hardware Information

---

### Post by coffeecat on 2009-11-22
> **jeb800e said:**
> System < Preferences < Hardware Information

That's not there in Karmic. Which package did you install to get that? Or is that in an earlier release of Ubuntu?

**emigrant**, try installing the package 'hardinfo'. Once installed you can run it from > Applications > System Tools > System Profiler and Benchmark.

---

### Post by jeb800e on 2009-11-22
It comes pre-installed in earlier releases.

---

### Post by XCan on 2009-11-22
It's not on my Jaunty machines. :/ I use Sysinfo from the repos.

---

