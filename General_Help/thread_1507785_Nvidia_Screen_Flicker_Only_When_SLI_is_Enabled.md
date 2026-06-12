---
title: "Nvidia Screen Flicker Only When SLI is Enabled"
date: 2010-06-12
forum: General Help
---

### Post by abeagley on 2010-06-12
Hi all,

I've tried both the x86 and x64 versions of Ubuntu 10.04 and installed the current Nvidia hardware drivers on both. Everything works fine until I enable SLI with the --sli=AFR or --sli=On

Once SLI is enabled there is extreme flickering relating to anything graphical. Including Compiz effects and any opengl software.

Disabling SLI returns the compy back to it's good self.

I would love to utilize SLI, however can't seem to find a solution for this bug.

Suggestions?

---

### Post by mbradlcu on 2010-12-04
I thought this was an linux/nvidia-driver issue since my system wasn't having the problem under windows. The fix for me was cleaning the sli connections and reseating the cable. Apparently this is a fairly common issue mentioned in the nvidia forums for windows users too.

---

### Post by pheedme_MTL on 2011-07-29
Greeting fellow earth Dweller. I had the Same Flickering Issues On My toshiba X200 (Satego) With Sli Set to on. I Cycled through the modes, until i found that SFR worked well with my system. Great performance and no flickering....


Be Prepared to Change the Values back  in the console, as some of the modes may not work for you, and in my case caused the desktop to be invisible. ( I tried AA, and then switched it to SFR, which works great )

Hope this Helps. Cheers.

SLI Modes :
To Quote "[Enlitend]("http://ubuntuforums.org/member.php?u=547171")"

sudo nvidia-xconf --sli=

The valid values for SLI are "Off", "On", "Auto", "AFR", "SFR", "AA", and "AFRofAA".

---

