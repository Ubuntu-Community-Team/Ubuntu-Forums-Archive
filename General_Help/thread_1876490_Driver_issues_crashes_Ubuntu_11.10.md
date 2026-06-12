---
title: "Driver issues crashes Ubuntu 11.10"
date: 2011-11-06
forum: General Help
---

### Post by gdjartov on 2011-11-06
Hey there,

a couple of days ago I installed graphic driver on my good old machine (apparently before that I didn't have properly installed drivers).

There were two options
 
 ATI/AMD proprietary FGLRX graphics driver [installed this one]
and
 ATI/AMD proprietary FGLRX graphics driver (post-release updates)

PC performance was great, until the moment I decided to watch a movie online - after 10 minutes the screen blacked out and I needed a restart. Any use that is more graphic intensive inevitably leads me to the black screen 

Deactivated ATI/AMD proprietary FGLRX graphics driver and tried to activate  ATI/AMD proprietary FGLRX graphics driver (post-release updates), but failed due to:

Sorry, the installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log

Then activated ATI/AMD proprietary FGLRX graphics driver, but the problem persists and now even without any streaming media the PC dies.

Would appreciate if you get me out of this pickle. 

Specs:
Ubuntu 11.10
[FONT=Arial, Helvetica, sans-serif][SIZE=2]- **HP Pavilion tx2500z Entertainment NB**
- AMD Turion(TM) X2 Ultra Dual-Core Mobile Processor ZM-82 (2.2 GHz)
- 12.1" diagonal WXGA High-Definition HP BrightView Widescreen (1280 x 800) w/Integrated Touch-screen
- 4GB DDR2 System Memory (2 Dimm)
- ATI Radeon(TM) HD 3200 Graphics
- 250GB 5400RPM SATA Hard Drive
- Webcam + Fingerprint Reader
- 802.11b/g WLAN and Bluetooth
- LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
- 8 Cell Lithium Ion Battery
- Microsoft(R) Works 9.0

[/SIZE][/FONT]

---

### Post by BillyBoa on 2011-11-06
I have the same problem and I fell that is a bug. :(

---

### Post by gdjartov on 2011-11-06
> **BillyBoa said:**
> I have the same problem and I fell that is a bug. :(

Have you tried activating the ATI/AMD proprietary FGLRX graphics driver (post-release updates?

---

### Post by Mark Phelps on 2011-11-06
I read that the repos version of the AMD drivers is 11.7 -- and that conflicts with 11.10.

Your best bet is to remove the AMD drivers (for now) and go with the default open-source drivers.  I'm using an ATI 4290 HD and the open-source drivers are very good in 11.10.  Get full resolution and multiple desktops -- not available in previous Ubuntu versions.

---

### Post by gdjartov on 2011-11-06
I've just removed the AMD drivers and will come back to report

---

### Post by gdjartov on 2011-11-07
The computer doesn't crash any more, but it is significantly slower than before :confused:

---

### Post by Mark Phelps on 2011-11-07
AMD has posted the Catalyst 11.10 drivers for Linux -- finally -- and I saw a thread recently where the poster said this version actually works.

So, you should go to the AMD site and download those drivers.

---

### Post by gdjartov on 2011-11-07
I've installed the Catalyst 11.10 drivers (form AMD's website), but I am back to where it all began - Ubuntu crashes and screen blacks out. I guess this will prove a bit trickier than I imagined

---

### Post by gdjartov on 2011-11-08
anyone?

---

### Post by gdjartov on 2011-11-09
Fresh install of 11.10 saved the day

---

### Post by jensoko on 2011-11-28
I'm having this same problem with Kubuntu 11.10. I have the same graphics card in my Thinkpad x100e (ATI Radeon HD 3200) and AMD Athlon Neo X2 Dual-core processors.

Just 2 days ago, I did a fresh install and had the same random screen blanks/system freezes. I tried using the ATI proprietary drivers, and that just makes the random system freezes happen at different times. 

I've turned off desktop compositing, and set my power devil to not blank or dim the screen in any mode.

I can't discern a pattern, and it's a real spirit-breaker. This thing's always been a bit finicky, but not since 10.04 have I had such issues with it.

---

### Post by UltimateCat on 2012-01-27
In 10.04 I lost all of my graphics and the ATI/AMD driver was working but the Catalyst Control Center kept telling me that the driver was not installed or not working properly.

This command helped me to get all of my graphics back:
```
 sudo cp /etc/X11/xorg.conf-backup-xxxxxxxxxxxx/etc/X11/xorg.conf

```

Then I restarted

The x's are of course the actual numbers in my file....everyones will probably be different

I hope this helps

---

