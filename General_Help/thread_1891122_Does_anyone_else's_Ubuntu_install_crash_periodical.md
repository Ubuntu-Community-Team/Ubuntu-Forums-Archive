---
title: "Does anyone else's Ubuntu install crash periodicaly?"
date: 2011-12-04
forum: General Help
---

### Post by Rsjc741 on 2011-12-04
Recently I installed Ubuntu 11.10 on my main 1TB drive to test drive the new Unity desktop interface.
However, I forgot how much of a hassle it was to get working... It's like trying to install OSX Snow Leopard again. (which, by the way, is easier.)

So now I'm left with a half-defunct system.

My main problem is in the title:

My machine freezes up.

I'd say I could get 2~5 hours of use at most. Though, if I let it be for some time, it will freeze. (20 minutes?)
Or sometimes while playing OpenTTD it will freeze up as well.

I got a couple of hunches as to why it does this, but if anyone has a solution it'd be greatly appreciated.





First off, my specs:

Intel Core i5 760 @ 2.87 Ghz LGA1156?
MSI H55M-E33 Motherboard (EU)
16GB DDR3 RAM
NVidia PNY GTX 560 Ti
1 TB HDD W/ Ubuntu 11.10
160GB HDD W/ Windows 8

Basically a mid-range gaming rig/ $700 ticker toy.




At first I thought it might be the way my Linksys WMP300N acts with NDISWrapper.. So i uninstalled that in favor for the Broadcom proprietary driver. 

Nada

Then I thought maybe Ubuntu doesn't play friendly with ACHI and APCI.

No again..

Maybe it was my C-State.

Still no.

I'm really at a whits ends here.

This has been a reoccurring problem on ALL Unix/Linux operating systems I've tried.

I need a stable system.

Any help?

---

### Post by oldtimer7777 on 2011-12-04
> **Rsjc741 said:**
> Recently I installed Ubuntu 11.10 on my main 1TB drive to test drive the new Unity desktop interface.
However, I forgot how much of a hassle it was to get working... It's like trying to install OSX Snow Leopard again. (which, by the way, is easier.)

So now I'm left with a half-defunct system.

My main problem is in the title:

My machine freezes up.

I'd say I could get 2~5 hours of use at most. Though, if I let it be for some time, it will freeze. (20 minutes?)
Or sometimes while playing OpenTTD it will freeze up as well.

I got a couple of hunches as to why it does this, but if anyone has a solution it'd be greatly appreciated.





First off, my specs:

Intel Core i5 760 @ 2.87 Ghz LGA1156?
MSI H55M-E33 Motherboard (EU)
16GB DDR3 RAM
NVidia PNY GTX 560 Ti
1 TB HDD W/ Ubuntu 11.10
160GB HDD W/ Windows 8

Basically a mid-range gaming rig/ $700 ticker toy.




At first I thought it might be the way my Linksys WMP300N acts with NDISWrapper.. So i uninstalled that in favor for the Broadcom proprietary driver. 

Nada

Then I thought maybe Ubuntu doesn't play friendly with ACHI and APCI.

No again..

Maybe it was my C-State.

Still no.

I'm really at a whits ends here.

This has been a reoccurring problem on ALL Unix/Linux operating systems I've tried.

I need a stable system.

Any help?

That looks like a nice rig.  I don't see anything that would necessarily cause this from your hardware specs alone.  Does this happen with 11.04?  If you leave a live stick of 11.04 booted from a usb flash drive overnight, what do the logs say?  Don't use any fancy desktop effects, and just have a clean system running and try to trace it down that way, because that is the way I have been able to figure out this same kind of issue before on other systems like your own.

---

### Post by Rsjc741 on 2011-12-04
My computer actually crashed while replying to you .. haha
If you could point me to where the log files are, ill post them on here or pm you and well go from there.

Does Ubuntu do well with ACHI or APCI?
I did an install off my W7/OSX overclock setting which has HPET, ACHI, and APCI all turned on. Ive also tried to see if the C-state was an issue. Tried both 3 and 1 to no avail.

---

### Post by oldtimer7777 on 2011-12-04
Do you have your BIOS set to default or simply refresh it from the CMOS switch yet? 

I would try to bring the system down to the bare minimum.   Leave a USB Live Stick of Ubuntu 11.04 running.. I would probably build a custom updated version with rematersys and use that to leave in there overnight.  Check the logs on the live stick, and see what they have to say, if it is still running at that point without a crash. 

Logs are here:

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

If you want to be really patient with it, you can install Htop and open that and watch to see what might cause it to crash as well.  It is kinda a hassle but you can sometimes catch it in the act. 

sudo apt-get install htop

> **Rsjc741 said:**
> My computer actually crashed while replying to you .. haha
If you could point me to where the log files are, ill post them on here or pm you and well go from there.

Does Ubuntu do well with ACHI or APCI?
I did an install off my W7/OSX overclock setting which has HPET, ACHI, and APCI all turned on. Ive also tried to see if the C-state was an issue. Tried both 3 and 1 to no avail.

---

### Post by Rsjc741 on 2011-12-05
Yes, I did a CMOS yesterday
I'll get back to you with that log.
 
I should be able to catch it mid-crash, since it just freezes.. it doesn't litterly crash.
 
And the BIOS settings mimic my "Optimized settings default" pretty much.

---

### Post by elmsly on 2011-12-13
Hi. I'm having the same problem on my newly built computer.

My hardware specs are
Intel i5 3.3GhZ CPU
Gigabyte Z68 motherboard
Asus GTX560Ti Graphics card
16GB Corsair 1600 MHz DDR3 Ram
Both the root filesystem and the home folders are on raid1 filesystems.

I notice we have the same graphics chip, I guess that may be the cause. In any case, my system crashes randomly, in a way that doesn't seem to correlate with what I do. The syslog, xlog and messages seem completely normal. I've tried running the gkrellm hardware monitor, and nothing seems out of whack when the system freezes. I'll try again with htop and see if that tells me something new.

---

### Post by Hylas de Niall on 2011-12-13
Yep.

Acer Aspire AX3812
Dual core Pentium e5400
3Gb RAM
Intel® G45/G43 x86/MMX/SSE2 on-board graphics and Realtek sound chips

---

### Post by BC59 on 2011-12-13
In what Ubuntu version you are having those problems?
We are in the second month of 11.10 life and we received an important flow of updates so far. After all these updates I assume the majority of important bugs, is already fixed. 

So having such serious problems the most logical explanation is that you have a failed installation. Your computer and Ubuntu have nothing to do with this. 

If you have such serious problems, then give it a try, download a fresh .iso file, burn it on a CD (not USB) and install it formatting all the partitions, /home included.

If you continue to have the same problems after the fresh install, please present it to the forum.

---

### Post by elmsly on 2011-12-13
I'm running 11.10. I have already reinstalled once in an attempt to get rid of this problem, to no avail.

---

### Post by BC59 on 2011-12-13
> **elmsly said:**
> I'm running 11.10. I have already reinstalled once in an attempt to get rid of this problem, to no avail.

Did you try to make it different? e.g. to download a new .iso, to burn a CD instead of using USB and most important, to format the installation partitions? Did you format your /home partition?

---

### Post by BC59 on 2011-12-13
If the problem is not fixed with the fresh installation you could try to install the kernel 3.1.4 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/)

---

