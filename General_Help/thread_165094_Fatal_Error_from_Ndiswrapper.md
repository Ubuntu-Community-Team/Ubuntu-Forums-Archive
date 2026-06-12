---
title: "Fatal Error from Ndiswrapper"
date: 2006-04-23
forum: General Help
---

### Post by jmorrow on 2006-04-23
Hoping someone can point me in the right direction.

I compiled the latest ndiswrapper yesterday and got everything working (surfing the net).  Today I turned my laptop on and got online, I then did some automatic updates advised by the pop-up. After re-booting I went to get online and there was no wireless showing. No prob I thought just re-modprobe ndiswrapper.  I thought wrong. The following error comes up anytime I try to 'sudo modprobe ndiswrapper'

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-21-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

The only change I can think of is I updated via the automatic updates. I am not sure why this would cause the problem I have.

Thanks in advance,
Jon](*,)

---

### Post by jmorrow on 2006-04-24
It turns out that the updates updated the kernel and that broke my ndiswrapper install.  I uninstalled ndiswrapper and reinstalled it. All is good now.

~Jon

:D

---

