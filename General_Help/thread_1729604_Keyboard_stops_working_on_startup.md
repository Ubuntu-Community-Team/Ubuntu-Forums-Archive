---
title: "Keyboard stops working on startup"
date: 2011-04-15
forum: General Help
---

### Post by troyguffey on 2011-04-15
Sometimes Ubuntu 10.04 will get into a state where the system stops booting when it apparently attempts to initialize the USB keyboard (keyboard goes dead and never lights up again)(Saitek Eclipse II keyboard).

It either works, or doesn't work consistently regardless of reboot.  I don't know what makes it stop working. (Or start working) Recovery mode doesn't work either.  Or the saved -21 kernal.

I have an ASUS M4A88TD-V EVO/USB3 and have the -30 generic kernal.

I can dual-boot into WinXP just fine.

---

### Post by Hippytaff on 2011-04-15
You can find boot information for usb devices by doing```
dmesg | grep -i usb
``` might shed some light on the issue.

---

### Post by troyguffey on 2011-04-15
It doesn't get far enough to type anything.  Like I said the keyboard goes dark, and doesn't come back.

USB Legacy support is enabled in the BIOS.

---

### Post by metalf8801 on 2011-04-15
Two things one make sure no keys are pressed before you see the BIOS screen. Two can you try using a PS/2 adapter? 

Not Play Station 2 see this link [http://www.newegg.com/Product/Product.aspx?Item=N82E16812200349&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Adapters+and+gender+changers-_-STARTECH-_-12200349](http://www.newegg.com/Product/Product.aspx?Item=N82E16812200349&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Adapters+and+gender+changers-_-STARTECH-_-12200349)

---

### Post by Hippytaff on 2011-04-15
> **troyguffey said:**
> It doesn't get far enough to type anything. Like I said the keyboard goes dark, and doesn't come back.
 
USB Legacy support is enabled in the BIOS.
 
I was thinking if you can get as far as the desktop (if your not required to log in) and you have this site bookmarked you could copy and paste the code from my post

---

### Post by troyguffey on 2011-04-15
As far as I can tell, there are no keys pressed.

No, I cannot try a PS/2 adapter.

---

### Post by troyguffey on 2011-05-31
New information:  Even attempting to boot from the Live CD (10.04 AND 11.04) has the same effect: i.e. Lockup.

---

### Post by Hippytaff on 2011-05-31
Odd - the whole desktop locks up or just the keyboard refuses to work?

---

### Post by troyguffey on 2011-05-31
I can't be sure because the screen is blank. I suspect it's not actually locked up, just waiting for the keyboard to be recognized, which rarely happens.

New information:  one of my disk partitions didn't get a clean exit, and Ubuntu will boot.  (with complaints, and a choice to skip mounting, or manual recovery)

---

### Post by troyguffey on 2011-06-07
Any ideas yet?

---

