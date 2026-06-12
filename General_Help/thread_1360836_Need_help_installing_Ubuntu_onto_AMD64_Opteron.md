---
title: "Need help installing Ubuntu onto AMD64 Opteron"
date: 2009-12-21
forum: General Help
---

### Post by benny148 on 2009-12-21
I recently won an AMD64 Opteron Workstation in my company's end of year computer lottery. The computer was completely wiped and came without an OS, so the first thing that came to mind was to install Linux.

I should preface this by saying that I'm extremely new to this, so bear with me.

Here are the specs of the computer (given to me by my company):

AMD Opteron, 1 GB Memory, 36 GB SATA Hard Drive, CDRW Drive, 64 MB Video Card, NO MODEM, NO OPERATING SYSTEM.

So I downloaded the Ubuntu Desktop 9.10 (32-bit) iso onto my other computer and burned the iso image to a CD using Infra Recorder. However, when I put the CD into the new computer, hit F9, and choose to boot from CD Drive, nothing happens.  After a few minutes I eventually get a "Non-system disk or disk error, Replace and strike any key when ready" error message. 

I'm not sure where to go from here.  I've burned the iso image twice to two different CDs and both times I got the same problem. Should I be using the 64-bit version? I didn't think it would matter, but maybe I was mistaken.

Any help would be greatly appreciated! Thanks in advance.

---

### Post by cascade9 on 2009-12-21
32 bit should work fine. As for if you should use 64 bit...maybe, maybe not, depends on who you ask ;) 

As for "Non-system disk or disk error, Replace and strike any key when ready" I would guess that your computer is still trying to boot from the hard drive, which being empty will lead to that error message. 

Try going into your BIOS and changing the boot order so that CD/DVD is 1st, then hdd is 2nd. There are a few variants on this (some BIOSes dont allow boot order, just bootable devices) so if you dont get a boot order option, dont panic! Just change the BIOS to allow booting from CD/DVD. Then, when the disc is in the drive, the computer should spin it up on starting, and you normally (but not always) will have a 'any key to boot from CD/DVD' message. Hit any key, and your on your way. ;)

---

### Post by prem1er on 2009-12-21
If your bios is able to boot from a usb drive and you have one handy you may want to get on a computer with internet access download and run a program called [unetbootin]("http://unetbootin.sourceforge.net/").  It will install the necessary files on your flash drive for you and then you can try booting from that. 

edit: +1 to the above poster.

---

### Post by reiki on 2009-12-21
also make sure you aren't burning the image by simply burning the iso to a CD. If you examine that CD it should not have just one file on it with an .iso extension.

Sorry if that seems obvious. I've seen it a ton of times :)

---

### Post by benny148 on 2009-12-21
Okay great, so my previous attempts at hitting F9, then choosing "boot from CD/DVD drive" is different than changing the BIOS?

Not sure if that question makes sense, I just want to make sure I'm heading in the right direction. 

Thanks!

---

### Post by benny148 on 2009-12-21
> **reiki said:**
> also make sure you aren't burning the image by simply burning the iso to a CD. If you examine that CD it should not have just one file on it with an .iso extension.

Sorry if that seems obvious. I've seen it a ton of times :)

Reiki - What should the CD have on it? I used Infra Recorder and selected "Burn Image" (using the directions here [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)).  Hopefully that's the right way to go...if not let me know! Thanks again everybody, this forum is fast!

---

### Post by cascade9 on 2009-12-21
I have had issues with doing the F9 trick in the past. It normally works, but not always. 

It is possible that reiki is right, and you have actually burnt the .iso as a data disc as well.

---

### Post by cholericfun on 2009-12-21
sounds like you did everything right i.e. burned the iso as image and booted off CD (F9 is the same as changing the bootorder only that its not persistent)

maybe try other install-cds like windows just to see if theres any reaction from the BIOS. (btw. go for the 64bit ubuntu for a permanent install)

have a good look at all your bios settings as well and maybe post stuff here that sounds suspicious.

and finally 
try unplugging the HD,
maybe put the cd-drive on a different connection as well.

PS: also try you CD out on different computers as "LiveCD" i.e. select "try this OS without any change to your Computer" on boot. 
just to see if it works

---

### Post by benny148 on 2009-12-21
> **cholericfun said:**
> sounds like you did everything right i.e. burned the iso as image and booted off CD (F9 is the same as changing the bootorder only that its not persistent)

maybe try other install-cds like windows just to see if theres any reaction from the BIOS. (btw. go for the 64bit ubuntu for a permanent install)

have a good look at all your bios settings as well and maybe post stuff here that sounds suspicious.

and finally 
try unplugging the HD,
maybe put the cd-drive on a different connection as well.

Great, thanks everybody for the help.  I'll check into everything this afternoon when I get home from work and post the results. I have an extra USB drive too, so I'll try unetbootin if all else fails.

---

### Post by cholericfun on 2009-12-21
> **benny148 said:**
> Great, thanks everybody for the help.  I'll check into everything this afternoon when I get home from work and post the results. I have an extra USB drive too, so I'll try unetbootin if all else fails.

Dont worry bout unetboot - try your cd as a LiveCD on your other computer and under System --> Admin you'll find a "create bootable USB" or something along those lines which will enable you to install from USB.
you may want to use a new USB or use the partition editor in the LiveCD to format your USB stick (make sure to select the right drive!) to fat32 i think.

you need 700MB space, if you wanted you can select to make a "persistant USB install" and give the "persistant part" some space. this allows you to boot other computers off the USB with settings and installed (/removed) programs saved at least on ***some*** computers. You may want to use 32bit Ubuntu for that to be able to do that on 32bit machines. I'd still recommend 64bit for the Opteron though. Actually thinking about it - check your BIOS to see if anything like boot from USB (external drive) is supported on your new machine.

---

### Post by benny148 on 2009-12-21
> **cholericfun said:**
> I'd still recommend 64bit for the Opteron though. Actually thinking about it - check your BIOS to see if anything like boot from USB (external drive) is supported on your new machine.

I know I remember seeing "boot from USB drive" or something of that nature when I hit F9.  I'll try the live CD on my laptop tonight and see if that works.  I just checked the CD and it's definitely not saved as a data file.  The disc is titled "Install Ubuntu" and it has quite a few folders and files on it (so I think it's correctly made).

So if the disc is correct, and it's still not working, maybe it's a problem with the CD Drive? I guess we'll know more later when I get home...

---

