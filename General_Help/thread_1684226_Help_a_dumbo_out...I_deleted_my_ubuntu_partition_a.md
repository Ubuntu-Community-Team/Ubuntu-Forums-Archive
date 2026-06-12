---
title: "Help a dumbo out...I deleted my ubuntu partition and now I can't boot into Windows"
date: 2011-02-08
forum: General Help
---

### Post by rachel22 on 2011-02-08
Hi,

So I'm a total non-geek, and am totally stuck. A long time ago, I installed ubuntu to dual-boot with windows 7, and everything was peachy. I recently decided to get rid of the ubuntu partition since I've got another laptop that I'm using exclusively for ubuntu (probably a bad decision, but I'm sticking with it.) I backed up the files I care about, and then I deleted all partitions (from windows) except the C:, leaving me with the C: and unallocated space.

Of course, when I go to boot up my computer, it gets stuck on the "loading...please wait" screen that it used to show before showing me my various boot options (several ubuntu ones, and then the windows loader at the bottom). It may say something else before loading, I can't tell since my screen is intact.

I suspect my windows 7 installation is still there, but I can't boot into it. I have an HP Pavilion DV2911. I have a live disk, but my optical drive no longer works. I *can* boot from USB (and load stuff onto a flash dive) but I don't know what to do. I have no recovery disk or partition, since I installed windows 7 myself, probably badly.

Where do I go from here? Is it a simple boot.exe or MSR error that I can fix? Did I do something worse than that?

Thanks for your help!

(And I recognize I'm posting on an ubuntu forum about windows, but it is sort of ubuntu-related. Also, you guys are smart and I don't expect the same from a windows forum.)

---

### Post by Smart Viking on 2011-02-08
I'm pretty sure that if you boot into the windows 7 repair disk(or something) it will be able to fix that, as you probably deleted grub and windows should be able to install it's MBR on it instead, that's what I would try. Boot it up and select whatever has "repair" eventually "auto repair" or something like that.

---

### Post by rachel22 on 2011-02-08
Unfortunately, my optical disk drive is broken, plus I have no windows 7 repair disk (I never made one, and my copy of windows was downloaded - legally - rather than purchased physically). Is there anything I could load onto a flash drive?

---

### Post by viktorzk on 2011-02-08
I suspect that it might be easiest to reinstall grub (the thing that shows you the various boot options).
You could install some linux live-cd on your usb (using, for example, the program "unetbootin" from your ubuntu laptop), boot into it, and install only grub. I don't know if this will work with a non-installable live-cd, so look for a small linux distribution, but not one that is designed to be run only from the live-cd.

---

### Post by Smart Viking on 2011-02-08
> **rachel22 said:**
> Unfortunately, my optical disk drive is broken, plus I have no windows 7 repair disk (I never made one, and my copy of windows was downloaded - legally - rather than purchased physically). Is there anything I could load onto a flash drive?
Dude, if you own a copy of windows 7 how can you possible feel guilty for downloading a new repair disk from wherever just to fix your system, you have paid for it and it's fair use to do that, don't think it's illegal, and if it is, something is very wrong about this world(I'm not sure whether it's legal or not, but c'mon, we live by rules that have no root in fairness - we should live by rules that makes sense).

---

### Post by IWantFroyo on 2011-02-08
Just ask for another copy of the recovery disk and give them your download code. According to Windows, you're entitled at least a CD that you could make into a USB.

---

### Post by rachel22 on 2011-02-08
That sounds doable. None of the flash drives I have lying around are more than 2gb, though, so I need something small - do you have an distribution recommendation?

And smart viking, I agree with you in theory but I quit illegal downloading after a scare last year and I'm not really keen on doing that, and I also feel uncomfortable in general downloading from shady sites. Plus, I wouldn't even know how to download a disk, especially given that I can't use a real 'disk'.

Edit: I guess I can call windows, but I would really prefer to keep my current installation intact if possible + not have to wait for the disk to get here. If that's my only option, though, I'll go with that.

---

### Post by viktorzk on 2011-02-08
I don't have a recommendation, sorry - I have never used a distribution smaller than Ubuntu. And if the download size isn't a problem, you could just use Ubuntu.

---

### Post by Bezukhov on 2011-02-08
Wow, I just had a *de ja vu* episode:
 
[http://www.bleepingcomputer.com/forums/blog/2199/entry-1728-quem-deus-vult-perdere-dementat-prius/](http://www.bleepingcomputer.com/forums/blog/2199/entry-1728-quem-deus-vult-perdere-dementat-prius/)

---

### Post by PRC09 on 2011-02-08
The repair disks are available below.As for using them on a usb using the usb program (in the second link below) not quite sure, but how to put your original disk on usb is available as well (for Windows)......I have used the repair disks but not the USB set-up so I am not much help other than that....

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

[http://sourceforge.net/projects/setupfromusb/](http://sourceforge.net/projects/setupfromusb/)

---

### Post by rachel22 on 2011-02-09
Thank you all for your help...after a frustrating few hours, I'm in again, windows intact.

Here's what I ended up doing, in case anyone references this thread later:
Created a system repair disk (this could be downloaded at the link above, but I created it legitimately with another 32 bit windows 7 computer, just with the windows utility)
Moved this to a bootable flash drive (thanks, 7-zip and iso recorder!)
Booted into that. First I ran the bootup repair thing, which was useless, but then I got into the command prompt and ran bootrec.exe/FixMbr
Within the blink of the eye, everything was fixed and I can now boot into windows like normal

Yay, I'm so happy - I was really scared that I would lose everything for a while. For a wannabee geek that really can't understand how anything works, this process was actually pretty fascinating. Thanks for your help, everyone!

---

