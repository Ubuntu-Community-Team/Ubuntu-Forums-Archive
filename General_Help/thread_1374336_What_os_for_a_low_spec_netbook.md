---
title: "What os for a low spec netbook"
date: 2010-01-06
forum: General Help
---

### Post by andru183 on 2010-01-06
Hey guys, my mates dad got a new ( yes new wait till you see the spec) netbook and wants some form of Linux on it. It's about 2ghz processor 64mb and no grafix card so resource wise what would be the best form of Linux, thanks for any input!

---

### Post by spcwingo on 2010-01-06
What make/model is it because I just don't see a new machine, netbook or not, only having 64MB of either HDD space or RAM.

---

### Post by llamabr on 2010-01-06
right.  There's no way you only have 64meg of ram.

But otherwise, a standard ubuntu install will work fine.  The install disk comes as a livecd which allows you to test it out before you install.  Pop it in and play around.  If you like it, install.  Then bring any problems or questions back here.

---

### Post by warfacegod on 2010-01-06
It's almost certainly a 64 MB video card. If there's no video card, then there's no picture. Guessing 1.5 GB RAM. Every netbook I've seen has an Atom and believe it or not the Atom processors are dual core. Ubuntu Netbook Remix should be just fine.

---

### Post by askreet on 2010-01-06
My bets on a 64GB SSD, and 1GB of RAM.

---

### Post by Ibidem on 2010-01-06
Agreed-you can barely find a 64 MB memory module; 2 GHz with that sounds ridiculous.  (IF it's PC compatible)
But if you're not kidding, those specs essentially mean "USE THE CLI!!"
If there's networking, I'd say MicroCore/TinyCore Linux; *perhaps* an old version of Puppy Linux, maybe Damn Small Linux (unmaintained, Linux 2.4), NimbleX might work; I once had Dapper running on a laptop with that much RAM and a ~500 MHz processor, and it was bearable with IceWM + AbiWord + Gnumeric.
What do you mean "no graphics card"?  If you mean a do-nothing integrated card, a light GUI might work; if it's really no card, you will never get ANY output (bios, boot, or GUI); if it's no VGA card, framebuffer (xfbdev) or xvesa *might* work; or are you going by diagnostic messages?
Most likely: 
Use Damn Small Linux
OR
TinyCore Linux
OR 
MicroCore Linux-- test text mode

In summary, it sounds like a project for a geek or a joke.

---

### Post by jmate24 on 2010-01-06
yeah, go with unr and try doing a usb install if it has no cdrom or dvd drive.

---

### Post by warfacegod on 2010-01-06
GUYS! It's got a ***_2 Ghz_*** processor. There's no way it's got only 64 MB RAM. The 64 he's seeing has got to video. Any normal Linux should work just fine.

---

### Post by Chronon on 2010-01-06
> **warfacegod said:**
> It's almost certainly a 64 MB video card. If there's no video card, then there's no picture. Guessing 1.5 GB RAM. Every netbook I've seen has an Atom and believe it or not the Atom processors are dual core. Ubuntu Netbook Remix should be just fine.

There are several different models of Atom processor.  The one in my netbook is single core, though it may be that all currently available (new) models are dual core (I haven't checked this recently).

---

### Post by Unhubbed on 2010-01-06
goto Unetbooting.com and download the program, it will open and give you all the variations of Ubuntu and choose 9.04, u must have a usb 1gb at the smallest and the program will download everything to usb, then power off computer, power back on goto boot menu then boot usb first, just move it up the list. save and restart with ur usb in computer, that should work Great...did for me. Im have an Acer aspire one D250-1842. Hope that helps

---

### Post by warfacegod on 2010-01-06
Okay. All the *new* Atoms are duals. That's what guy at the compy shop was telling me anyway.

---

### Post by PhilGil on 2010-01-06
The OP is most likely mistaken about the RAM or the processor specs.  I'm wondering if he has one of those 7 inch, ARM processor, Win CE netbooks that you can find on ebay...
[http://cgi.ebay.com/Laptop-NOTEBOOK-NETBOOK-Epc-7-2G-64MB-Portable-SKU165_W0QQitemZ330391821834QQcmdZViewItemQQptZUS_Netbooks?hash=item4cece31e0a](http://cgi.ebay.com/Laptop-NOTEBOOK-NETBOOK-Epc-7-2G-64MB-Portable-SKU165_W0QQitemZ330391821834QQcmdZViewItemQQptZUS_Netbooks?hash=item4cece31e0a)

There's a recent thread on this site about trying to get Linux running one one of these (so far, it doesn't look like the posters have had much luck):
 [http://ubuntuforums.org/showthread.php?t=1349626](http://ubuntuforums.org/showthread.php?t=1349626)

---

### Post by warfacegod on 2010-01-06
[SIZE="3"]andru183[/SIZE]

Would you be kind enough to go into the netbook's BIOS and report back with what it says it's got for hardware?

---

### Post by warfacegod on 2010-01-06
Looks like your last post got yanked for being rude andru183. That's ok, I read it before it was gone. This is your netbook.

```
Processor : AK7802Q216 248MHz:
Display : 7&#8221; High resolution TFT .(800 x 480 pixels)
Internal Memory : DDR 64MB / 2GB Nand-flash
External Memory : SD card , U-Disk , USB-HDD
Connectivity :
WIFI RIEEE 802.11 b/g
Ethernet RJ-45
Connections :
- USB 2.0 x 1 (supports external memory)
- USB 1.1 x 2 (supports keyboard & mouse only)
- SD / MMC card slot (up to 8GB)
- Microphone jack x 1
- Earphone jack x 1
- DC jack x 1
```

Plus at the bottom, it say "no good for flash web pages". Next time you want help, report your specs accurately, you told us it had a 2 Ghz CPU, that's over 8X faster than it actually is.

---

### Post by Ibidem on 2010-01-08
The processor is ARM architecture... *maybe* ubuntu/debian "armel" would work.
Make sure to get at least a 2-4 GB SD card; otherwise, you will be in a tight squeeze.

Ibidem

---

