---
title: "Install Remix on regular laptop"
date: 2010-01-14
forum: General Help
---

### Post by apperrault on 2010-01-14
Hi everyone,
I am not sure if i missed a post somewhere, but my search didn't turn up anything.  Does anyone know if it is possible to install the Ubuntu Remix on a laptop that doesn't have an Atom processor?  I have a small form-factor laptop, but it isnt a Netbook, that i would love to install Ubuntu Remix on, but for some reason it hangs when i try and install it.  Does anyone know if it is possible to install this release on a standard laptop?  Are there links somewhere that i could follow?

thanks much

app

---

### Post by pirateghost on 2010-01-14
> **apperrault said:**
> Hi everyone,
I am not sure if i missed a post somewhere, but my search didn't turn up anything.  Does anyone know if it is possible to install the Ubuntu Remix on a laptop that doesn't have an Atom processor?  I have a small form-factor laptop, but it isnt a Netbook, that i would love to install Ubuntu Remix on, but for some reason it hangs when i try and install it.  Does anyone know if it is possible to install this release on a standard laptop?  Are there links somewhere that i could follow?

thanks much

app
burn the iso, or stick it on a bootable thumb drive, boot, install...its that easy

i have UNR installed on my sons latitude d430 and it runs GREAT!

---

### Post by apperrault on 2010-01-14
I was afraid you were going to say that.  I guess i have some system problems with my laptop then.  Standard Ubuntu installs just fine, but the Remix has problems.  I will keep playing with it.

thanks

app

---

### Post by snowpine on 2010-01-14
An Atom processor is not required (many netbooks like the original Asus EEE don't have Atom) so long as you meet the minimum system requirements you should be okay:

[https://help.ubuntu.com/community/Installation/SystemRequirements#Netbook%20alternative%20%28Ubuntu%20Netbook%20Remix%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Netbook%20alternative%20%28Ubuntu%20Netbook%20Remix%29)

If you can install "regular" Ubuntu, I think you can then install the Netbook interface by installing the 'ubuntu-netbook-remix' package. Good luck!

---

### Post by apperrault on 2010-01-14
I got it to work.  for some reason it was failing on the USB install, but once i burned the ISO to a disk, i got it to work.  

thanks

app

---

### Post by dvn3ch on 2010-01-27
There are two things that I can see that may have caused your problem.  


[LIST=1]
[*]Some laptop BIOS have the option of booting from USB but fail in the actual execution of it.  What I found in a Sony LT that I had was that the BIOS was looking for something specific (i.e. windows MBR) but when fed the UNR boot code from a USB stick it did not want anything to do with it.  I would blame this on lazy BIOS programming.  Newer LT and NB have (for the most part) resolved this.
[*]Not all USB sticks are created equal.  I have three USB sticks that all have the same UNR installed on them.  However, two work as they should and one does not.  I have found that the fancier the USB stick the harder it is to get the boot action to work; even after completely "wiping" the stick clean.  I get the cheap, buy-them-by-the-dozen USB sticks from Newegg or Geeks.com.  I have had great luck with them.
[/LIST]
That's my two cents.

---

