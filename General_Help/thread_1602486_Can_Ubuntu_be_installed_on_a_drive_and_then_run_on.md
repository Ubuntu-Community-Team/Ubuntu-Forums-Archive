---
title: "Can Ubuntu be installed on a drive and then run on ANOTHER computer?"
date: 2010-10-21
forum: General Help
---

### Post by Andy06 on 2010-10-21
I'm trying to install Ubuntu on old desktops without proper optical drives (they half work, its hit and miss) and the BIOS does not allow booting from the USB.

Can I yank the HDD out, install Ubuntu (with bootloader) on it using it as an external drive on another computer and then plug it back in?

Would there be any problems? 

Thanks

---

### Post by pqwoerituytrueiwoq on 2010-10-21
you can transplant a hard drive and have ubuntu still boot there is a chance you may need to edit the boot path on the other system in gurb
the only way i have seen to have any issues is use a proprietary driver on one system and not the other
i would not yank it out i would be more gentle with it hdd's are fragile

---

### Post by wkulecz on 2010-10-21
I've had very good success (can't actually recall a serious issue, in fact)doing this with all flavors of Linux, although it was very much more difficult in the old days of setting up X windows by editing xorg.conf (or what ever).

As he said above, Grub issues are likely to be the major issue these days when doing this as long as the target system will function without some driver you have to download and patch.

---

### Post by Andy06 on 2010-10-21
1) I am installing the GRUB bootloader to the same HDD partition as the Ubuntu install. Then I will use the computer BIOS to point to that particular HDD as the boot drive. Perfect solution?

2) It is possible to install multiple drivers to enable full functionality on all computers right? (like ATI drivers AND Nvidia drivers)

---

### Post by Mark Phelps on 2010-10-21
> **Andy06 said:**
> 2) It is possible to install multiple drivers to enable full functionality on all computers right? (like ATI drivers AND Nvidia drivers)

IF you're talking about proprietary drivers, I believe the answer is NO.  When you boot from the drive, it will use the last proprietary driver you installed.  If that is incompatible with your video card/chip, you are likely to get either a console, or a black screen with a blinking cursor.

Know of no way to install a bunch of different proprietary video drivers and expect the OS to pick the correct one on startup.

---

### Post by C.S.Cameron on 2010-10-21
It is neatest if you disconnect the internal drive from the computer you use to install or else do a update-grub once it is back in the old machine.
You should install the boot loader to sda not sda1.
When you install a proprietary video driver it removes any previous proprietary video drivers.
You can install what drivers you want once you have it back in the old machine.

---

### Post by Andy06 on 2010-10-21
> It is neatest if you disconnect the internal drive from the computer you use to install or else do a update-grub once it is back in the old machine.
You should install the boot loader to sda not sda1.
When you install a proprietary video driver it removes any previous proprietary video drivers.
You can install what drivers you want once you have it back in the old machine. 

You said to install the bootloader to sda not sda1. 
sda would be ideal when each OS occupies a whole disk and the BIOS is used to point to them right?

Earlier I used to make Vista/7 and Ubuntu dual boots with booth installs on the same disk with the Windows bootloader as the managing entity (using EasyBCD), so in THAT case, the ideal place for the bootloader to go would be the Ubuntu partition right? (sda1, sda2, sda"X")

Also in the new Ubiquity installer, how do I set the bootloader location preference? The option is buried under manual/advanced and if I select it there and go BACK to "easy install" to use entire disk, will that setting be lost?

ATI cards work out of the box, since they come pre-installed, I suppose they're not considered proprietary?

Thanks guys

---

### Post by StiltonSandwich on 2010-10-21
When I wanted to install Ubuntu on an old computer that would not boot from a CD, I had success using [_Smart BootManager_]("http://sourceforge.net/projects/btmgr/"). You boot into it from a floppy disk, and it allows you to choose a drive to boot from (such as the CD-ROM drive). The UI is terse and unhelpful, but it does the job.

Obviously this is no good if the computer doesn't have a floppy drive, or you cannot find a working floppy disk (an increasingly rare object these days). But it's another option, if you need it.

---

### Post by efflandt on 2010-10-21
> **Andy06 said:**
> 2) It is possible to install multiple drivers to enable full functionality on all computers right? (like ATI drivers AND Nvidia drivers)

If you are going to be moving a drive from computer to computer (like a USB drive), it would be best to stick with default drivers which cooperate with each other as long as you do not need anything special.  ATI or Intel may boot with proprietary nvidia driver installed, but will complain and will not be as fast as without the proprietary nvidia driver which would interfere with their glx.  But I hear the nvidia card might not work with proprietary ATI drivers.

So if you are installing on one PC for use on another PC, wait to install any proprietary video drivers until the drive gets to its final home PC (or any other special drivers on destination).  Although, certain special wireless drivers (like Broadcom) may just be ignored if booted on a PC with no Broadcom device.

---

### Post by C.S.Cameron on 2010-10-21
> **Andy06 said:**
> You said to install the bootloader to sda not sda1. 
sda would be ideal when each OS occupies a whole disk and the BIOS is used to point to them right?

Earlier I used to make Vista/7 and Ubuntu dual boots with booth installs on the same disk with the Windows bootloader as the managing entity (using EasyBCD), so in THAT case, the ideal place for the bootloader to go would be the Ubuntu partition right? (sda1, sda2, sda"X")

Also in the new Ubiquity installer, how do I set the bootloader location preference? The option is buried under manual/advanced and if I select it there and go BACK to "easy install" to use entire disk, will that setting be lost?

ATI cards work out of the box, since they come pre-installed, I suppose they're not considered proprietary?

Thanks guys

Once you get to manual partitioning why not set your partitions there instead of going back to easy install?
I have had best luck selecting sda for the bootloader no matter which partition the O/S(s) is/are on.

---

