---
title: "AMD unsupported hardware?"
date: 2010-04-14
forum: General Help
---

### Post by chisle on 2010-04-14
In the corner of my screen it says "AMD unsupported hardware" this is while under ubuntu 10.04 beta 2. i was wondering how do i figure out more details like maybe what exactly is unsupported and what can i do to get that off the corner of my screen? thanks

---

### Post by darolu on 2010-04-14
This is why you should not use Lucid Beta in working environments. It is not fully supported yet.

Try posting here: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by mcduck on 2010-04-14
> **chisle said:**
> In the corner of my screen it says "AMD unsupported hardware" this is while under ubuntu 10.04 beta 2. i was wondering how do i figure out more details like maybe what exactly is unsupported and what can i do to get that off the corner of my screen? thanks

That message tells you that you are trying to run Ati/AMD proprietary video card drivers on a video card that isn't supported by those drivers.

Remove the fglrx driver and use the open-source radeon driver (the defalt one in Ubuntu) instead.

The message is in no way related to running development release of Ubuntu.

---

### Post by chisle on 2010-04-14
i'm guessing if i just remove the proprietary driver it will automatically use the open source driver?

---

### Post by mcduck on 2010-04-14
> **chisle said:**
> i'm guessing if i just remove the proprietary driver it will automatically use the open source driver?

Yes, that should do it, but you might want to check /etc/X11/xorg.conf (if the file exists) and remove anything the fglrx driver might have put there.

..actually if you haven't done any manual configuration in that file, and it exists on your system, you can safely just delete the whole file. It doesn't exist in the default install and everything will be just automatically detected unless otherwise configured in that file.

---

### Post by doas777 on 2010-04-14
I have several boxes that have ATI HD4200's which are not supported by the restricted driver in ubuntu, and show this watermark. 
the solution is to download and install the driver from ATI themselves. see here for more info

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mcduck on 2010-04-14
> **doas777 said:**
> I have several boxes that have ATI HD4200's which are not supported by the restricted driver in ubuntu, and show this watermark. 
the solution is to download and install the driver from ATI themselves. see here for more info

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

That could be the other option if chisle's graphics card is *too new* for the fglrx version.

If it's too old (meaning pretty much anything else than Radeon HD series) then no version of fglrx will support it.

---

### Post by doas777 on 2010-04-14
> **mcduck said:**
> That could be the other option if chisle's graphics card is *too new* for the fglrx version.

If it's too old (meaning pretty much anything else than Radeon HD series) then no version of fglrx will support it.

actually these just fell through the cracks. the 3850 and 4200 are motherboard integrated, so they seem to be considered in a separate class. they aren't really new or old at present. no idea if this is the kind of card chisle has, but these two are the only ones I've ever heard of producing that watermark, but I'm sure there are others.

---

### Post by mcduck on 2010-04-14
> **doas777 said:**
> actually these just fell through the cracks. the 3850 and 4200 are motherboard integrated, so they seem to be considered in a separate class. they aren't really new or old at present. no idea if this is the kind of card chisle has, but these two are the only ones I've ever heard of producing that watermark, but I'm sure there are others.

most of the old cards will also produce the same watermark if you try to use fglrx drivers.

---

### Post by chisle on 2010-04-14
> **doas777 said:**
> actually these just fell through the cracks. the 3850 and 4200 are motherboard integrated, so they seem to be considered in a separate class. they aren't really new or old at present. no idea if this is the kind of card chisle has, but these two are the only ones I've ever heard of producing that watermark, but I'm sure there are others.
yea i am using integrated graphics. its the HD4290 IGP from the new AMD 890 chipset.

---

### Post by doas777 on 2010-04-14
> **chisle said:**
> yea i am using integrated graphics. its the HD4290 IGP from the new AMD 890 chipset.
well then, hopefully the driver from ati.com will do you. post back if you have trouble getting it installed.

---

### Post by danieleday on 2010-08-17
I have the same problem with a new install on a GA-890GPA-UD3H motherboard (integrated Radeon HD 4290 graphics). Did you have any luck with a downloaded driver set? If so, which version did you try?
Cheers

---

### Post by YUMESUKI on 2010-11-11
MSI 890GXM-G65 with ATI HD4290 integrated

Though the watermark says unsupported, this is false.

With the open source drivers Neverwinter Nights (Linux client) shudders badly even on the lowest settings
With fglrx driver NWN runs at max framerate on ALL settings

The only issue is the watermark . . . is there a way to just disable this??

Have heard installing via Catalyst works, true?
------------------------------
SOLVED

Manually installing works
[]("http://support.amd.com/us/gpudownload/Pages/index.aspx")[]("http://support.amd.com/us/gpudownload/Pages/index.aspx")Catalyst 10.10
Xubuntu 9.10
Kernel 2.6.31-22 generic

Catalyst packages are [HERE]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
Instructions I used are [HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually")


Lesson learned; Ubuntu repositories are unreliable . . . when in doubt, do it the GNU/Linux way! Learn to term . . .

---

