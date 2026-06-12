---
title: "Ubuntu won't start.. black screen.. all after a update"
date: 2011-08-24
forum: General Help
---

### Post by Mattsface on 2011-08-24
Hey guys

I run a Ubuntu dual boot system @ home. Windows 7 on one hard disk and Ubuntu on the other. Everything was going fine until I started updating the drivers and software on the Ubuntu partition.

My computer starts up fine and I am able to select which OS I want to run... Windows 7 starts up with no issues when I select my Ubuntu OS I get a blinking cursor *top left*, then a black screen....nothing and when I hit the shutdown button on my desktop tower I see a purple screen with the ubuntu logo and then the machine shuts down.

I can boot into a failsafeX mode or whatever fine but not sure what to do from there?

oh and its the 64 bit!!

My specs are as follows
Q6600, P5N-D motherboard, 2 GBs of memory(had 6GBs :(:( ), Radeon 6970 and a XFI sound card

---

### Post by Mattsface on 2011-08-24
bump ;)

---

### Post by decoherence on 2011-08-24
Was the update process interrupted?

Boot in to ubuntu however you are able and run

sudo apt-get -f install

if you have a network connection, run 

sudo apt-get update && sudo apt-get upgrade

as well. Otherwise, just reboot and hope you get a little bit further. 

If it doesn't install anything else, I guess that's not the problem.

---

### Post by Kisbey on 2011-08-24
Similar issue here.  11.04 64-bit as well, radeon hd6950, phenom 1090T, 16G.
 
Failsafe works, as do root network prompt, etc.   
 
Updates are fine, nothing interrupted, resetting repositories yeilds no change.
 
Symptoms:  System boots normally, loads grub, goes to a purple screen, then black, and hangs.
 
This began after an update yesterday.  I suspect X, as I think I saw an update there yesterday.  System loads and runs grub just fine.  /var/log/Xorg.0.log indicates that the fglrx driver is the last thing to load.  Running the latest catalyst 11.8 drivers.  These drivers were working prior to yesterday's update.  I've not tried downgrading video drivers.
 
Interstingly, the behavior differs subtly depending on what kernel I use on boot.  Selecting an older kernel, my power button and crtl-alt-f2, etc., seem to work.  On the latest build, my computer is hard locked; cycling power is necessary to restore activity.  I don't think the kernel is the problem, but it's an interesting data point.

---

### Post by Mattsface on 2011-08-24
I'll be home from work soon Kisbey

we might have the exact same thing going on.. because I also installed the catalyst 11.8 drivers then the issue began

---

### Post by corbsie on 2011-08-24
This all started after doing the suggested updates as well today. This is my first post and I'm not sure if I'm posting in correct space. If I need to open my own thread let me know.

My Ubuntu machine is in a constant loop trying to boot. It starts to  boot, goes to the GNU GRUB screen, for a nano second, and immediately tries to boot again.  Over and over again.

If I hammer down on the down arrow key I can  get it to stop at the GNU Grub screen but any option results in a constant  loop happening again.

So I created an installation Disc and an installation Flash drive using Ubuntu main website. Neither helps the machine  progress farther when I select them from the  Boot menu, which I can access/same as the Bios.

I've also tried  two separate hard drives. One with Ubuntu on it and the another one clean out  the packaging. I was trying to just do a fresh install to fix it as I am 2 months into my first Linux machine.

Does any have any thoughts on this issue or how to attack the problem? 
I've been googling and reading for the past 2 hours. I got the machine to boot of the disc once in "try Ubuntu without installing" mode. IT worked. I then tried installing from there but it fails. Any help would be great and I'm sorry if  I hijacked your thread.

---

### Post by Kisbey on 2011-08-24
Corbsie, I don't think there's enough info yet to know whether this is the same problem or not.  It sounds like a different problem, but I'd stick around and see if someone has some advice.  Out of curiousity, are you using an ATI or AMD graphics card, and if so, what graphics driver?  Are you using a 64-bit distro?  The more info we have, the more likely someone will have a "eureka" moment and propose a fix.

---

### Post by byal9000 on 2011-08-24
Sorry, a newbie here.

I was having what appeared to be the same problem as the OP just after I updated. I rebooted, and got not much of anything. It would load until the screen turned purple, I would get the Ubuntu logo (which is more than everyone else I think), and then it would hang there for more than an hour if I let it.

I logged onto my Win7 partition and found this thread which gave me the idea to reinstall my graphic drivers. I've got an NVIDIA card, so I logged onto Linux using  the Failsafe mode, downloaded the latest drivers from NVIDIA, and installed them.

After that, I got past the Ubuntu logo and everything is working the way it should be. Hope that this little bit of information helps.

---

### Post by Kisbey on 2011-08-24
For the record, this is looking like an issue between the graphics driver and a recent X- Server update.  Removing the catalyst drivers on my system permitted a normal boot with the open source drivers. My next step will be to boot with catalyst 11.7 instead of 11.8; I'll update after that test.

Edit: X-server loads normally on Catalyst drivers, version 11.7, but fails to load on 11.8; this behaviour is new after yesterday's update.  Again, this is 64-bit only.  I cannot speak for the other issues posted here.  Prior to that update, 11.8 was working flawlessly.  Since the fixes in 11.8 are negligible, I don't personally have a lot of impetus to go back over to 11.8 and troubleshoot there.  I suspect the fix is going to turn up in another x-server update or a new catalyst build.  Something that might be tried is to uninstall the x-server updates from yesterday and see if 11.8 works again... it's a pretty safe bet that it would.  Any suggestions on the best way to accomplish this?

---

### Post by corbsie on 2011-08-24
> **Kisbey said:**
> Corbsie, I don't think there's enough info yet to know whether this is the same problem or not.  It sounds like a different problem, but I'd stick around and see if someone has some advice.  Out of curiousity, are you using an ATI or AMD graphics card, and if so, what graphics driver?  Are you using a 64-bit distro?  The more info we have, the more likely someone will have a "eureka" moment and propose a fix.

Thanks Kisbey.

I have an ASUS EAH5450 [http://usa.asus.com/Graphics_Cards/AMD_Series/EAH5450_SILENTDI512MD2LP/](http://usa.asus.com/Graphics_Cards/AMD_Series/EAH5450_SILENTDI512MD2LP/)

It is an ATI graphics card. I typically have to download the drivers for me to get the correct aspect ratios for my Sanyo 56 inch TV. I utilize the HDMI output. 

I was using the 32 bit distro of Ubuntu.

I have currently reformatted the hard drive in EXT3 format with 2GB Linux Swap partition using Acronis Disk Director 11.

I have also removed both sticks of 2GB DDR II RAM and my CMOS battery to hopefully 'clear' any memory.

When I boot from CD it still Cycle boots. Occasionally I get the "grub rescue>" but I am really bad with command prompt commands so I have been googling and reading forums.

I feel like something happened to my motherboard, a Gigabyte GA G33m-S2l,[http://www.gigabyte.com/products/product-page.aspx?pid=2692&dl=1#ov](http://www.gigabyte.com/products/product-page.aspx?pid=2692&dl=1#ov)

Thanks for responding. I appreciate it.

---

### Post by Kisbey on 2011-08-25
Corbsie, it sounds like the problem is not with the graphics drivers or the x-server.  If you're reaching the bootloader only to see it immediately reboot, that's likely to be something else.  Grub should either pause and wait for an entry or timeout after ~8 seconds or so.  I don't know if there's a way to adjust the timeout, but it sounds like that's not something you would have altered and I'd list that as a low probability regardless.

The common thread here seems to be that you also have an amd/ati card, but if you're stuck at the boot loader neither the graphics drivers nor the x-server have loaded yet, so the likely culprits for the other issues in this thread are ruled out by default.  A possibility is the graphics card itself, but since you're seeing grub it sounds like its doing its job and making colored pixels on the screen, so again, we're probably looking at something else.  

You may want to start another thread and focus instead on the bootloader behaviour.  Good luck!

---

### Post by corbsie on 2011-08-25
> I have currently reformatted the hard drive in EXT3 format with 2GB Linux Swap partition using Acronis Disk Director 11.

I have also removed both sticks of 2GB DDR II RAM and my CMOS battery to hopefully 'clear' any memory.Doing this stopped my cycle boot and it took a fresh install of Ubuntu, obviously as I LLF it as well.

Do we know which update causes the problem so I can avoid it?

---

### Post by Kisbey on 2011-08-25
> **corbsie said:**
> Do we know which update causes the problem so I can avoid it?
 
No.  I suspect something with Xserver, but I've not dived deep enough into the logs to start ripping out updates to see which one triggered the issue on my end.  I may try and tackle this tonight if I have time.
 
Glad to hear you're making progress.  At the same time, however, the issue you originally described was taking place before the system tried to load X, so I'm not sure yours is the same issue.  YMMV...

---

