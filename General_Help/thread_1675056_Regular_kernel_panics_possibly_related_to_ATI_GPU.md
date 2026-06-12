---
title: "Regular kernel panics possibly related to ATI GPU"
date: 2011-01-24
forum: General Help
---

### Post by Drostin77 on 2011-01-24
Hello, got kernel panics :)!

**Summary**

[LIST]
[*]Ubuntu Desktop Edition 10.10 32 bit
[*]ATI Radeon HD 4670
[*]Dual Screen setup
[*]Kernel panics
[/LIST]

**Story**
[INDENT]I have a machine (specs below) that had been running Arch Linux stably for about 2 years.  Then the (nvidia) GPU died, and so I swapped in an ATI I had was using (stably) in another computer (the other computer has an ion so it can do OK w/ out GPU). I was running XMonad under Arch, and I could not get XMonad + the ATI drivers (open source or proprietary) to play nice w/ my dual screen setup.  However, I did not have any kernel panics under my Arch Linux setup (this makes me think the problem is not broken hardware).[/INDENT]

[INDENT]Having been using Ubuntu at work recently and having had it work great, I decided to install it.  Immediately my dual monitors were correctly recognized, it "just worked". It was great. Then the screens turned all black except for the (non-moving) cursor and my caps-lock and scroll-lock lights started blinking.  I rebooted and "ack"ed around in /var/log but didn't find anything.  Hoping it was a fluke, I installed Awesome 3 and it "just worked", it was great.  Then I had another black-screen + non-moving cursor and blinking keyboard lights.  Thinking it might be the video card driver I switched from open-source ATI driver to proprietary driver.  It seemed to work for about 3-4 minutes and then everything froze.  However, with the proprietary driver the screen did not turn black, everything just stopped responding, and keyboard lights started flashing.  Again, I didn't find anything suspicious "ack"ing around /var/log.[/INDENT]

[INDENT]Since I am not very far along with this install I figure I might as well reinstall tonight (Tokyo time), but I have a suspicion the problem will remain.[/INDENT]

[INDENT]I'm not even sure where I should be looking, my kernel-panic troubleshooting knowledge pretty much ends at "Check in /var/log".  Any help will be appreciated, any further information I can provide I will provide if I can as quickly as I can.  It is my experience on both Windows and Linux, but especially Linux, that ATI drivers are unstable so I'm hoping this is software not hardware, and if possible I would like to solve this without buying new hardware (of course if the hardware is broken I'll give in :).  At the least I'd like to confirm the cause is indeed the GPU before buying a new one.  Thanks in advance!  [/INDENT]

**Specs**

[LIST]
[*]Mobo: MSI 975X Platinum V.2 LGA 775 Intel 975X ATX
[*]CPU:  Intel Core 2 Duo E4300 Allendale 1.8GHz LGA 775 65W Dual-Core Processor BX80557E4300CPU: 
[*]Memory: A-DATA 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model AD2U800B1G5-DRH
[*]GPU: HIS Hightech H467QT512P Radeon HD 4670 IceQ Turbo 512MB 128-bit GDDR3 PCI Express 2.0
[*]PSU: FSP Group SAGA+ 400R 400W ATX12V Power Supply
[*]2 x Western Digital Caviar SE16 WD7500AAKS 750GB 7200 RPM SATA 3.0Gb/s 3.5"
[*]monitor 1:  SCEPTRE X24WG-1080P Black 24" 2ms Widescreen LCD Monitor
[*]monitor 2: Acer....... 24" (sorry will get specs later if needed!)
[*]DVD Drive: Don't remember (can get specs if needed)
[/LIST]

---

### Post by Drostin77 on 2011-01-25
Crashes were caused by on-board Ethernet port.  Switching to pci ethernet card made system stable.  (Driver for pci ethernet card not found so card is not working, but thats a seperate issue).

---

### Post by Drostin77 on 2011-01-27
> **Drostin77 said:**
> Crashes were caused by on-board Ethernet port.  Switching to pci ethernet card made system stable.  (Driver for pci ethernet card not found so card is not working, but thats a seperate issue).

Just kidding.  While the ethernet card was ALSO a problem, the kernel panics remain.  I have no re-installed ubuntu 10.10 (from a different, freshly downloaded) iso, and have installed nothing but updates.  I am back to black-screen and non-responsive cursor crashes and continue to not find anything overly suspicious in /var/log.  Any ideas?

---

