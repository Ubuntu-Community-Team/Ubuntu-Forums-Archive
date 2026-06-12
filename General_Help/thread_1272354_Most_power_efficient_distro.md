---
title: "Most power efficient distro"
date: 2009-09-22
forum: General Help
---

### Post by tushar_t on 2009-09-22
For a laptop, would Xubuntu offer a significant increase in battery life compared to Ubuntu? Theoretically it should given that it's running Xfce, but I tried searching for benchmarks and couldn't find any. 

If there's not much difference between Xubuntu and Ubuntu in terms of power consumption, could you please offer me any other suggestions? How about Crunchbang for instance? 

Thanks!

---

### Post by Oak37 on 2009-09-22
This [article]("http://www.linux-mag.com/cache/7520/1.html") might help you. Lubuntu might be more aimed at what you want. What was really surprising was how badly Xubuntu fared against Ubuntu in the memory usage comparison.

---

### Post by sideaway on 2009-09-22
heard of [wattos]("http://www.planetwatt.com/")?

---

### Post by P4man on 2009-09-22
A desktop environment (even an OS) is not likely to make much, if any difference. The "big" issues influencing battery life would be:
- cpu scaling working properly. Should work on any *buntu
- videocard not being stressed unnecessarily -> disable desktop effects.

Now if you're RAM constrained (512Mb or less), I imagine a lighter OS would help, as it would result in less harddisk activity (which costs battery life), but don't expect miracles.  Perhaps xfce is also slightly less cpu intensive, but I would be very surprised if that would result in a measurable difference in battery life.

If you want a very simple trick to (slighly) increase battery life: use a dark theme. And reduce your LCD brightness.

---

### Post by tushar_t on 2009-09-22
> **P4man said:**
> A desktop environment (even an OS) is not likely to make much, if any difference. The "big" issues influencing battery life would be:
- cpu scaling working properly. Should work on any *buntu
- videocard not being stressed unnecessarily -> disable desktop effects.

Now if you're RAM constrained (512Mb or less), I imagine a lighter OS would help, as it would result in less harddisk activity (which costs battery life), but don't expect miracles.  Perhaps xfce is also slightly less cpu intensive, but I would be very surprised if that would result in a measurable difference in battery life.

If you want a very simple trick to (slighly) increase battery life: use a dark theme. And reduce your LCD brightness.
I see, so I shouldn't expect anything more than a few minutes here and there unless the hardware itself is changed. Yes my RAM is only 512MB, so I'll go for a lighter OS anyway, even if it only slightly improves the battery life. Cheers.

> **Oak37 said:**
> This [article]("http://www.linux-mag.com/cache/7520/1.html") might help you. Lubuntu might be more aimed at what you want. What was really surprising was how badly Xubuntu fared against Ubuntu in the memory usage comparison.
> **sideaway said:**
> heard of [wattos]("http://www.planetwatt.com/")?
Excellent guys, thanks. Is wattos stable given that it's still in beta?

---

### Post by tushar_t on 2009-09-22
Another question: where exactly can I get Lubuntu from?

---

### Post by bryncoles on 2009-09-22
> **tushar_t said:**
> Another question: where exactly can I get Lubuntu from?

Currently, its not a live cd (wait till the end of October for that). Or, install the LXDE metapackage from synapitic, then choose that session from the log in screen. 

I think in theory you should also be able to install the minimal environment from the alt CD, then type "sudo apt-get install lxde" or something like that to install it without all the crud and extra's of a regular ubuntu install.

---

### Post by tushar_t on 2009-09-22
Cool, I think i'll try WattOS until the Live CD comes out.

---

### Post by 01000111 on 2009-09-22
> **tushar_t said:**
> Cool, I think i'll try WattOS until the Live CD comes out.

I have found that DSL running on a minimal config system (512MB) runs considerably faster and hits the hdd so infrequently that it goes to sleep.  That alone should save some power.

---

### Post by nortexoid on 2009-09-22
Take a look at [this article]("http://www.anandtech.com/mobile/showdoc.aspx?i=3642") and observe the horrible power consumption of Jaunty compared to various flavors of Windows. It's enough to switch back to Windows.

---

