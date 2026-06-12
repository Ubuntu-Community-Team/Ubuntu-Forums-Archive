---
title: "grub/ubuntu + lilo and another disro?"
date: 2009-07-09
forum: General Help
---

### Post by muteXe on 2009-07-09
Afternoon all,
My laptop is 100% ubuntu. I want to now dual boot it with another distro.  When the other distro asks me if i want to install LILO, do i say "no thanks", and just add another entry in my grub menu to give me the option of booting into this distro?
Or is there something I'm missing?

Cheers,

mute

---

### Post by danwood76 on 2009-07-09
Yes thats how to do it.
You cant have both grub and lilo on the same disk.

---

### Post by muteXe on 2009-07-09
Cool.  
Cheers ears.

---

### Post by andrew.46 on 2009-08-18
Hi danwood,

> **danwood76 said:**
> Yes thats how to do it. You cant have both grub and lilo on the same disk.

Mind you for a very long time I had lilo installed to the *MBR *loading Slackware on one partition and then chainloading Ubuntu on another partition. The ubuntu partition had grub installed to the *root of its own partition* rather than the MBR thus releasing me from the painful task of reconfiguring lilo each time Ubuntu updated the kernel.

Sounds a bit complex but in fact quite straightforward to setup and bulletproof to run...

Andrew

---

### Post by danwood76 on 2009-08-18
> **andrew.46 said:**
> Hi danwood,



Mind you for a very long time I had lilo installed to the *MBR *loading Slackware on one partition and then chainloading Ubuntu on another partition. The ubuntu partition had grub installed to the *root of its own partition* rather than the MBR thus releasing me from the painful task of reconfiguring lilo each time Ubuntu updated the kernel.

Sounds a bit complex but in fact quite straightforward to setup and bulletproof to run...

Andrew

Yes you are correct.
I infact have grub and GAG loaded into partitions and the MBR.

The reason I said that was to not confuse the issue as you have done.

---

### Post by andrew.46 on 2009-08-18
Hi danwood,

> **danwood76 said:**
> The reason I said that was to not confuse the issue as you have done.

You are quite correct and I apologise for muddying the waters more than a little.

Andrew

---

