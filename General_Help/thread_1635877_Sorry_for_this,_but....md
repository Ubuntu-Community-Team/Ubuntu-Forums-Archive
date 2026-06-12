---
title: "Sorry for this, but..."
date: 2010-12-02
forum: General Help
---

### Post by edward1978 on 2010-12-02
Ubuntu 10.04 has drove me nuts freezing, I upgraded to 10.10 & no help. I was wondering about switching distoes, but I saw a post saying most major distroes freeze also. So can anyone list ones that don't freeze. I do love Ubuntu, but 4 months of it has driven me nuts with the freezes. I had OpenSuSE 10.3 on the same system for a year, no probs. at all.

---

### Post by philinux on 2010-12-02
> **edward1978 said:**
> Ubuntu 10.04 has drove me nuts freezing, I upgraded to 10.10 & no help. I was wondering about switching distoes, but I saw a post saying most major distroes freeze also. So can anyone list ones that don't freeze. I do love Ubuntu, but 4 months of it has driven me nuts with the freezes. I had OpenSuSE 10.3 on the same system for a year, no probs. at all.

I'm assuming you've activated your graphics driver.

System>admin>additional drivers.
Selecting the recommended.

---

### Post by kanishkdudeja on 2010-12-02
post the output of 

```
top
```

in 10.10 or 10.04..

u hav a good configuration..it should not freeze.

---

### Post by peyre on 2010-12-02
If you're unclear what philinux is talking about, click on "Hardware Drivers" or "Additional Drivers" in your Applications menu.  It's probably under System.  I'd be more specific about all this, but the details differ between the various distros (Ubuntu vs. Xubuntu & 10.10 vs. 10.04, etc.).  If you see our video driver in there, you'd tell it to Activate it--that's likely to do the trick.  Hopefully you won't have to go through a manual installation of the driver--that's a pain.

Another option is to try another version of Ubuntu.  I've had two older laptops which didn't like regular Ubuntu or Xubuntu (probably because of the graphics cards), but worked well with Lubuntu.  You might even try a different version number.  My current laptop runs great in Lubuntu 10.04, but won't keeps logging me out in 10.10.

---

### Post by edward1978 on 2010-12-02
> **philinux said:**
> I'm assuming you've activated your graphics driver.

System>admin>additional drivers.
Selecting the recommended.

Nope, they are off.

[http://img249.imageshack.us/i/screenshotdy.png/](http://img249.imageshack.us/i/screenshotdy.png/) Top pic.

Lubuntu huh, ok, but I should beable to handle Gnome. I have a good system.

EVGA. nForce 650i ultra Intel Core 2 Duo Wolfdale E8200 2.66GHz 
6MB Cache Dual Core 1333MHz  4 Gig DIMM-DRAM NVIDIA GeForce 8800 GTS with 512 DDR3 memory (PCIe 1.00 x16)

---

### Post by philinux on 2010-12-02
> **edward1978 said:**
> Nope, they are off.

[http://img249.imageshack.us/i/screenshotdy.png/](http://img249.imageshack.us/i/screenshotdy.png/) Top pic.

Lubuntu huh, ok, but I should beable to handle Gnome. I have a good system.

EVGA. nForce 650i ultra Intel Core 2 Duo Wolfdale E8200 2.66GHz 
6MB Cache Dual Core 1333MHz  4 Gig DIMM-DRAM NVIDIA GeForce 8800 GTS with 512 DDR3 memory (PCIe 1.00 x16)

Select the recommended driver and choose activate.

---

### Post by Jouke74 on 2010-12-02
Hi you can always try Debian stable. That distro is a bit older, but also very unlikely to have freezing problems after a basic install. Leave your adjustments to the system to a minimum. 

Before you do this I suggest that you run Memtest86+ (should be an option in Grub). Random freezes are often caused by bad memory or a "dis-communication" (wrong settings) between the motherboard and the internal memory.

---

### Post by TBABill on 2010-12-02
Just out of curiosity about your issue...is this a laptop? I'm asking because mine randomly goes from in use or idle right to a bright white/grayish colored screen and you cannot do anything other than shutdown OR I can close the screen (shut the lid), open it, close it, open it....then it comes up as if it were asleep or in hibernate. Once I enter password it picks right back up (but wireless has to reconnect). It's completely random and happens in Mint 9, Mint 10, Ubuntu 10.04 and Ubuntu 10.10 (yes I know those Mint versions are built off of the Ubuntu versions listed). 
 
Do you experience screen freezing where whatever you see stays frozen or does it switch like mine to another look as if a video card crashed? My machine is cool and even cooler now that 2.6.32-26 is out so it is not a heat issue (although a failing sensor could act like an overheated machine).
 
Just asking to clarify what you are having happen and to give an example of what mine is doing for comparison. Mine is random, sometimes when it is just sitting idle with no power settings enabled.

---

### Post by peyre on 2010-12-02
> **edward1978 said:**
> Nope, they are off.

[http://img249.imageshack.us/i/screenshotdy.png/](http://img249.imageshack.us/i/screenshotdy.png/) Top pic.

Lubuntu huh, ok, but I should beable to handle Gnome. I have a good system.

EVGA. nForce 650i ultra Intel Core 2 Duo Wolfdale E8200 2.66GHz 
6MB Cache Dual Core 1333MHz  4 Gig DIMM-DRAM NVIDIA GeForce 8800 GTS with 512 DDR3 memory (PCIe 1.00 x16)

It isn't really a matter of the quality or power of your system, but whether the Linux distro in question likes/supports your video card--that is, whether it's friendly with the video card.  In my case, the newer laptop had plenty of beef to run Ubuntu--it ran XP just fine, for instance.  But for whatever reason, Ubuntu and Xubuntu just wouldn't boot--or even install.  IIRC, they *would* install and boot with an older version (pre-10.04), but I wanted at least 10.04.

---

### Post by kanishkdudeja on 2010-12-03
@edward..

the output of top seems okay..

i thnk u shud try out what philinux has said..activate the recommended missing driver..:)

---

### Post by edward1978 on 2010-12-03
> **philinux said:**
> Select the recommended driver and choose activate.

I uninstalled the nvidia packages yesterday, I did have the recomended enabled & I was freezing. The uninstalling didn't help, still freezes. :(

> **TBABill said:**
> Just out of curiosity about your issue...is this a laptop? I'm asking because mine randomly goes from in use or idle right to a bright white/grayish colored screen and you cannot do anything other than shutdown OR I can close the screen (shut the lid), open it, close it, open it....then it comes up as if it were asleep or in hibernate. Once I enter password it picks right back up (but wireless has to reconnect). It's completely random and happens in Mint 9, Mint 10, Ubuntu 10.04 and Ubuntu 10.10 (yes I know those Mint versions are built off of the Ubuntu versions listed). 
 
Do you experience screen freezing where whatever you see stays frozen or does it switch like mine to another look as if a video card crashed? My machine is cool and even cooler now that 2.6.32-26 is out so it is not a heat issue (although a failing sensor could act like an overheated machine).
 
Just asking to clarify what you are having happen and to give an example of what mine is doing for comparison. Mine is random, sometimes when it is just sitting idle with no power settings enabled.

I have a desktop, the screen stays how it, I get times when the mouse just freezes & other times system wide. If it helps, here's my spec. 
EVGA. nForce 650i ultra Intel Core 2 Duo Wolfdale E8200 2.66GHz 
6MB Cache Dual Core 1333MHz  4 Gig DIMM-DRAM NVIDIA GeForce 8800 GTS with 512 DDR3 memory (PCIe 1.00 x16).

Oh & I did a memtest, no error were found on a long run. Is there a system monitor for ubuntu, you know CPU usage, temp, memory & vid. card iusage. So I can see if anything gets strange at freeze? It would be good for output to be on the Gnome system bar (the top one).

---

### Post by Swagman on 2010-12-03
Coincidence ?

[http://forums.overclockers.co.uk/showthread.php?t=18213380](http://forums.overclockers.co.uk/showthread.php?t=18213380)

---

### Post by Spyderkid on 2010-12-03
I recommend that you enable the driver 

then if that doesn't work a re-installation of Ubuntu might be worth a try

also if that doesn't work I know people will probably say this isn't the case but you may have a malicious piece of software on there, If you've downloaded stuff from the internet and made them executable this can be possible there are only  700-800 linux viruses out there, but you might of been one of an unlucky few.

---

### Post by edward1978 on 2010-12-03
Ok haha "I am not a linux genius", LXDE is OMG bad is there any other light waight DE? I like the gnome look any like that.

---

