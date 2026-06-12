---
title: "Overclocked pc won't boot ubuntu 10.10/10.04 live cd"
date: 2011-02-24
forum: General Help
---

### Post by rusty725 on 2011-02-24
Hi All,
I got a problem with Ubuntu 10.10/10.04 x64 I can't initial boot. I get kernel machine check exception error (kernel panic not syncing reboot in 30 secs)
My pc is overclocked to 4.4, speedstep, CxE,Execute Disable Bit -disabled, Hyperthreadin -disabled, Turbo Boost Enabled aka multiplier -enabled Vt-enabled.
Weird stuff: Ubuntu works fine under vmware 7.1.3 build-324285 and show cpu clock 4.2 without multiplier(which is fine with me even though the multiplier's enabled)
I disabled multiplier and Ubuntu boots fine; however,
it won't show overclocked speed instead it shows 2.6mhz. 

specs:
cpu core i7 920 do (overclocked 4.4 passed with Linx/Prime95 )
ram corsair 6gb 2000mhz (overclocked from 8-8-8-24-1T to 7-7-7/18-64-1T 1700mhz)
gpu asus 460gtx (not overclocked)
1 ssd crucial 300c 64gb (bios set to AHCI {non raid system} )
2 hdd western digital 750gb
psu corsair 850W

---

### Post by rusty725 on 2011-02-25
tried Parted Magic 5.9 i686 and it boots fine even sees overclock without multiplier. so what's up with ubuntu ?

[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

---

### Post by hfranco75 on 2011-05-22
Same here with Natty. Windows 7 boots and performs perfectly when my i7 920 @ Asus P6TD Deluxe is overclocked at 3.2 GHz, but Ubuntu crashes while booting (kernel panic). Please Help!!!

---

### Post by linuxinstalledfromhdd on 2011-05-22
I would try resetting the over-clocking configuration changes you have made to the default recommended manufacturers specifications and try again.  It might not be just the overclocking that is causing this issue. It could be a combination of other factors.

---

### Post by hfranco75 on 2011-05-22
> **linuxinstalledfromhdd said:**
> I would try resetting the over-clocking configuration changes you have made to the default recommended manufacturers specifications and try again.  It might not be just the overclocking that is causing this issue. It could be a combination of other factors.

The system is fully functional while using the default config. The problem is only present when trying to boot Ubuntu after modding the MoBo to overclock it at 3.2 GHz. With the same config, Windows boot OK and is totally stable. The problem could be in the default Natty kernel, maybe it is not prepared to work under OC settings, I guess

---

### Post by linuxinstalledfromhdd on 2011-05-22
Excellent.

---

### Post by hfranco75 on 2011-05-22
Answer below

---

### Post by hfranco75 on 2011-05-22
> **linuxinstalledfromhdd said:**
> Excellent.
Not excellent at all... if Window$ is working flawless with those O.C. settings, Ubuntu should work well too... but as soon as I change something in the BIOS O.C. configuration, Ubuntu becomes unusable because the kernel refuses to boot... any idea?

---

### Post by linuxinstalledfromhdd on 2011-05-22
Bump

---

### Post by pyn on 2011-06-18
same here, kernel panic.  at stock settings everything's fine.

Edit:  except for the fact that I'm using 11.04 installed to my hd.

---

### Post by rusty725 on 2011-07-20
alright guys I found a solution it is a kernel fault or to be correct the way the kernel is configured. I downloaded fixed kernelcheck from webupd8 site and messed with cpufreq and acpi options and it worked. I'm now using kernel 2.6.39.3 x64 with 4.4ghz oc. I also found that latest distro of Crunchbang linux boots just fine with overclocked pc at 4.4ghz and it uses some old kernel 2.6.32 x64

---

