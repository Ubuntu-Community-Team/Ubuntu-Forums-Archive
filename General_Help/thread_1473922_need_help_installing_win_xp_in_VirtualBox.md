---
title: "need help installing win xp in VirtualBox"
date: 2010-05-05
forum: General Help
---

### Post by aCsbD6N5xj on 2010-05-05
Hi.

I'm using ubuntu 10.04 (upgraded from 9.10) and i've also got my WinXP Toshiba Rescue CD which i'd like to install in VirtualBox but it just won't go past the 'unpacking' part. When it says that it's completed, the only option i have is clicking OK. Doing that just shuts down the VM then. And when i restart the VM, it just does the unpacking step all over again.

Last year when i had a dual boot system (XP and ubuntu 8.10 i think it was), the installation went fine until i realized that my ubuntu partition was waaay too small. So i could not install XP in a VM. But it still got to the actual windows installation step.

And yes I'm still using the same PC the rescue CD came with.

Any suggestions?

Thx

---

### Post by dv3500ea on 2010-05-05
You can't install into a virtual machine from a recovery CD - you need an installation disk :(

---

### Post by phibit on 2010-05-05
@dv3500ea is right, you need an installation disk.

Be aware that running Windows XP in a VM actually violates the EULA.

---

### Post by aCsbD6N5xj on 2010-05-05
> **dv3500ea said:**
> You can't install into a virtual machine from a recovery CD - you need an installation disk :(

sh*t. coz i actually made a custom XP install CD when i still had XP installed, which only included XP and not the companion bloatware. 

I forgot to test the iso before burning it and switching to ubuntu. When i tried using it in Virtualbox, or just try to actually boot from that CD when i switch my PC on, it just won't work.

---

### Post by aCsbD6N5xj on 2010-05-05
> **phibit said:**
> @dv3500ea is right, you need an installation disk. You can usually "borrow" an iso of Windows XP Pro w/ serial from BitTorrent.

Be aware that running Windows XP in a VM actually violates the EULA. "Borrowing" an .iso from BitTorrent is also heavily frowned upon. If you can find a version of Windows XP that matches your existing serial number, that's your "best" options from a legal perspective.


Warez OS - Thanks but no thanks

EULA - No one's gonna know anyways so I don't really care.

So that custom CD i mentioned was supposed to work coz it only had the boot and installation stuff but it just won't work, whether in a VM or actually booting it. What could possibly be missing? Coz i could still modify the iso file i guess

---

### Post by bapoumba on 2010-05-05
No advocating piracy, thanks.

---

### Post by drdos2006 on 2010-05-05
[http://pcsupport.about.com/od/windowsxp/f/download-windows-xp.htm](http://pcsupport.about.com/od/windowsxp/f/download-windows-xp.htm)

---

### Post by aCsbD6N5xj on 2010-05-06
> **drdos2006 said:**
> [http://pcsupport.about.com/od/windowsxp/f/download-windows-xp.htm](http://pcsupport.about.com/od/windowsxp/f/download-windows-xp.htm)

thx for the link. guess there's no solution then. i'll just rely on WINE *gasp*

anyways here's the link where it shows that XP Custom CD thing:

[http://www.howtohaven.com/system/createwindowssetupdisk.shtml](http://www.howtohaven.com/system/createwindowssetupdisk.shtml)

Did anyone have any luck with that?

I still have mine which doesn't work btw

---

### Post by kio_http on 2010-05-11
See my tutorial here.
[http://ubuntuforums.org/showthread.php?t=1322436]("http://ubuntuforums.org/showthread.php?t=1322436")

---

### Post by aCsbD6N5xj on 2010-05-29
> **kio_http said:**
> See my tutorial here.
[http://ubuntuforums.org/showthread.php?t=1322436](http://ubuntuforums.org/showthread.php?t=1322436)

Thx for the thread.

I have one qs: I only have 512mb RAM (Virtualbox says 496) and VB won't let me use more that half of the existing RAM. Is that an issue for the later steps? (I know it's stated in the thread that XP needs a minimum of 256mb RAM)

---

### Post by howefield on 2010-05-29
> **BucketBob said:**
> I only have 512mb RAM (Virtualbox says 496)

You are really kidding yourself if you plan on virtualising xp in Ubuntu with 512 megabytes of RAM.

---

### Post by aCsbD6N5xj on 2010-05-29
> **howefield said:**
> You are really kidding yourself if you plan on virtualising xp in Ubuntu with 512 megabytes of RAM.

Really ??? Too slow??? :confused: 

I really need to use MS Office.

I can't even install it through WINE now that I'm using ubuntu 10.04. I can't mark the install file as executable coz it's on a CD. It just says it's not possible coz it's read-only.

---

### Post by mkvnmtr on 2010-05-29
I installed xp 3 or 4 times with 300Mb allowed and it ran fine. I could just never find anything to do with it so I deleted it each time. If you have to run all that virus stuff that might not be enough ram.

---

### Post by InfinityEleven on 2010-05-29
try some more ram.

---

### Post by Yellow Pasque on 2010-05-29
> **phibit said:**
> Be aware that running Windows XP in a VM actually violates the EULA.
Even when that's the only place you install it?

---

### Post by howefield on 2010-05-29
> **phibit said:**
> Be aware that running Windows XP in a VM actually violates the EULA.

Perhaps you'd be accurate enough to point out the relevant section of the EULA ?

---

### Post by ronnielsen1 on 2010-05-29
I have xp running smooth in virtualbox but ONLY after upgrading my box to 2 gig and giving xp 1 of them

---

### Post by wilee-nilee on 2010-05-29
Since you have the OEM recovery you might as well dual boot this will fix the problem, and make sure that you are within the user agreement with MS. A install in a virtual which is probably not legal, then installing MS word leaves you out in the wind to lose the use of either, if detected. No moral judgment here just a logical resolution to your problem.

---

### Post by aCsbD6N5xj on 2010-05-29
Ok Here is the part I'm stuck at: 

For the first picture, there was actually another window that stated the 'successful file unpacking'. I already pressed OK beforehand.

With the second picture, it just shows the DOS prompt and the VM then 'powers off'. When I restart it, I have to go through the unpacking again.

When I was dual-booting Ubuntu 8.10 and windows, I was able to go past  that step in VB (in ubuntu), and go through the actual windows installation process. But ultimately my ubuntu partition was too  small.

@mkvnmtr: What virus stuff are you talking about? Did you mean anti-virus? I won't be running those. Only MS office, provided my VM won't run too slow.

@wilee-nilee: I disable network adapters in my VM so no risk here.

@everyone reading: If MS allows a legal XP license to be used virtualized in XP mode (Win7), why is it not legal with VBox, regardless of the host OS?

---

### Post by howefield on 2010-05-30
> **BucketBob said:**
> @everyone reading: If MS allows a legal XP license to be used virtualized in XP mode (Win7), why is it not legal with VBox, regardless of the host OS?

It is interesting that the posters posting this rubbish, (imho) have yet to do so with some credible information to back it up.

---

### Post by aCsbD6N5xj on 2010-05-30
[http://en.wikipedia.org/wiki/Virtual_pc](http://en.wikipedia.org/wiki/Virtual_pc)

So yeah, I guess it can be concluded from this that there's nothing really illegal about virtualizing legal XP licenses, coz it's from MS itself!

Unless I missed something? The only 'difference' is I'm using an OEM rescue CD which must be why virtualisation doesn't work in the first place.

---

