---
title: "date &amp; time wrong"
date: 2010-03-05
forum: General Help
---

### Post by hazman on 2010-03-05
When i boot up ubuntu 8.10 the time and date are a month behind.Is there anyway of correcting this?

---

### Post by maddg3241 on 2010-03-05
can't you edit it by clicking on it

---

### Post by plucky on 2010-03-05
Also check the settings in the BIOS.

Good Luck

---

### Post by DexterP17 on 2010-03-05
Are you connected to the internet? If you aren't then connect to the internet and that should fix the problem. and go to your preferences to see if it has automatic sync in your area.

---

### Post by ratcheer on 2010-03-05
Run

ntpdate time-b.nist.gov

Tim

PS - That command must be run under sudo to work.

---

### Post by hwttdz on 2010-03-05
And I like ntpd to keep the time up to date without you having to worry about it.  It's like a magic clock.  Now if only my radio alarm clock didn't drift by days...

---

### Post by maddg3241 on 2010-03-05
ya i forgot to mention if you are not connected to the internet then you will not get an accurate time

---

### Post by hatalar205 on 2010-03-05
> **hazman said:**
> When i boot up ubuntu 8.10 the time and date are a month behind.Is there anyway of correcting this?
Probably you have a dual booted machine (windows and Ubuntu). I had such kind of a problem for a few times in another distro, and only once under Ubuntu. Probably your auto update is open in Windows clock. At first just launch clock application under Windows, update your time settings (if it doesn't work try other time servers) and after correcting disable "auto-update", and then you'ii never have a problem like that.

---

### Post by lyall on 2010-03-05
how old is your PC/Laptop?

PC/laptops that are older than 4 years some times the CMOS battery is getting weak. 

the CMOS battery is located on the motherboard
it is about the size of a quarter

good luck and have fun learning

---

