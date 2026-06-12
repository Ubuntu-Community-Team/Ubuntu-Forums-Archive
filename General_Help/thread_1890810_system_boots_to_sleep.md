---
title: "system boots to sleep"
date: 2011-12-04
forum: General Help
---

### Post by elliotn on 2011-12-04
I am extremely stressed at this point, my 11.10 boots to a blank non responsive manner.

1. I get to grub 
2. I choose ubuntu 
3. instead of Plymouth bootscreen appearing the monitor goes blank and LG logo runs around like the pc is off or sleep.

if I boot to rescue mode and choose the option RESUME NORMAL BOOT it boots without any problem. 

please help

---

### Post by CharlesA on 2011-12-04
Need more info on the machine.

Sounds like a video driver problem, to be honest.

Also moved to GH.

---

### Post by elliotn on 2011-12-04
my machine is an BioStar G31-m7, onboard gfx card Intel GMA 3100

---

### Post by CharlesA on 2011-12-04
Have you made any changes to the OS since this started happening?

---

### Post by elliotn on 2011-12-04
> **CharlesA said:**
> Have you made any changes to the OS since this started happening?

no I didn't do any changes at all

---

### Post by CharlesA on 2011-12-04
> **elliotn said:**
> no I didn't do any changes at all
Hmm, Was there an update before this started to happen?

---

### Post by elliotn on 2011-12-05
> **CharlesA said:**
> Hmm, Was there an update before this started to happen?

no updates and if I check for updates it says my system is up to date,

---

### Post by elliotn on 2011-12-05
matter silved easly

here is how:
my graphic card is intel 82g33  but my system was using NVIDIA drivers, so I went to synaptic and searched for any NVIDIA related driver that is installed and removed it. rebooted and it worked

---

