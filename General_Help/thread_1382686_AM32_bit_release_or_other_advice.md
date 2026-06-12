---
title: "AM32 bit release or other advice?"
date: 2010-01-16
forum: General Help
---

### Post by Questor_ix on 2010-01-16
The problem:  I am a poor man who until today was running WinXP on AMD64 using an old usb wireless wusb11v4 adapter (32 bit drivers).

I have recently installed the Ubuntu 9.10 AMD64 release.  It looks very nice.  

But I cannot use ndiswrapper to load my 32 bit wusb11v4 driver because of the 64 bit os vs the 32 bit driver.

I can hardly buy a new wireless adapter.  But I do not see an AMD32 bit release.  

Any advice?

---

### Post by Vaphell on 2010-01-16
just install i386 version which is 32bit. amd64's are backwards compatible and they run 32bit OS just fine. amd64 is just a common name for 64bit version of x86 architecture (x86_64), introduced first by amd. Now almost any modern mainstream processor can run amd64 labeled OSes, just like they are able to run legacy 32bit oses (i guess your XP was 32bit).

---

### Post by bsh on 2010-01-16
or set up a 32bit chroot for ndiswrapper and run it from there?

---

### Post by Questor_ix on 2010-01-16
Ok, I'll simply downgrade to 32bit.  I don't plan on doing anything that requires horsepower, instead I'll basically just be piddling in OpenOffice and the net.  

Thanks folks.

---

