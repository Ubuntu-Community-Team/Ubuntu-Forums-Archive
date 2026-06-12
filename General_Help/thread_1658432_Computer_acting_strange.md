---
title: "Computer acting strange"
date: 2011-01-02
forum: General Help
---

### Post by klingzw on 2011-01-02
It all started about a week ago, I heard a grinding noise coming from the computer (never good)... Long story short it ended up being a bad PSU fan. I replaced that and all seemed to be fine until I started to get an error message after bios stating "system fan has failed" Looking in the case I noticed that the rear exhaust fan is moving rather slowly, so I replaced that as well. The new rear exhaust fan is also running slowly and I am still receiving the "system fan failure" error. I checked the system fan terminal on the MoBo and am receiving ~4.5volts which is rather strange as I believe it should be around 12v.

So I lived with the "system fan failure" because I monitor all temps, and nothing was out of the ordinary.

I then attempted to upgrade from Ubuntu 10.04 64 bit to 10.10 via update manager (I know bad idea) the download went fine, but when I rebooted, I could not get back to the desktop. Thankfully I backed everything up!

So I used my linux mint flash drive (very handy) to open a live session and wipe my ubuntu hard drive clean. Since I have been enjoying linux Mint I took the opportunity to partition my Linux hard drive and install Mint 10. No issues with the install and it is currently running fine. I then attempted to reinstall Ubuntu 10.04 LTS via the CD that I originally used months ago. 

This is where the strange part comes in... It takes about 15min (actually timed) to go from a bios screen to the Ubuntu 10.04 live cd desktop. If I open firefox and or try to install via the desktop icon the screen goes black and then I am at a log in screen being prompted for a user name and password. On occasion it will even reboot the computer.

I am just baffled at what has caused this issue. 

System specs

AMD 5600+ processor (dual core at 2.8GHZ)
3GB DDR2 800 Ram
Nvidia 8600GTS video card
80GB IDE hard drive dedicated to Ubuntu 
500GB Sata Had drive for Windows 7 as well as general storage
500watt PSU

No recent changes besides the fan issues. Was running perfectly up until this event.

O... I also did a memory test and all 4 dims (2x1gb and 2x512mb) tested good.

I realize that this is a rather long post, but I just wanted to give as much background information as possible. Any ideas or thoughts would be appreciated.

Thank you, 
                Zach

---

### Post by no2498 on 2011-01-03
you may try putting some new heat sink compound for the processor
it may have gotten to hot with the other fans  gone bad
if it still does not like to restart
i would try a new power supply unit
they can take out the mother board if just not the right power

hope something i said helps you

---

### Post by Yellow Pasque on 2011-01-03
> I checked the system fan terminal on the MoBo and am receiving ~4.5volts which is rather strange as I believe it should be around 12v.

Is this in the BIOS or after booting OS? If latter, it may be normal and due to fan speed control.

---

### Post by klingzw on 2011-01-03
I was getting 4.5 v in the bios with a calibrated digital multi meter, which is why I am rather concerned that there may be a mobo issue. 

I highly doubt that there is any issues with the processor, as when I am in windows all operations are at normal speed and temps. I am suspect of the PSU as well, I just hated to replace it if there was an under lying software issue with the Live CD. My thinking is that there maybe an issue that when running the live CD, I need to power the ram, processor and CD drive to max power and the PSU cannot keep up with it.


Thanks, 
           klingzw

---

### Post by Yellow Pasque on 2011-01-03
It may be a short somewhere in the mobo (which would put a high load on the PSU). IDK, but something gives me the feeling that if you keep running it, it's going to "give up the ghost" or more bluntly, release the magic smoke.

---

