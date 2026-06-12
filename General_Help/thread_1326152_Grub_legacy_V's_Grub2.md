---
title: "Grub legacy V's Grub2"
date: 2009-11-14
forum: General Help
---

### Post by marcopolo1981 on 2009-11-14
Can anyone tell me what the benefit of using Grub2 is?

Using Grub Legacy, on reboot, I see the bios screen for a second or two, then less than a second later I have the grub menu where I can select which system to boot into. The screen renders itself almost instantly.

Using Grub2, again on reboot, I see the bios screen for a second or two, then spend about 4 seconds watching the grub2 menu render itself before it lets me interact with it.

Personally, I can't see any improvement with the new Grub. In fact, I'd say it was the opposite. It slows my boot process, all be it only a few seconds.
I know it has support for having pretty pictures, and all that, but that is no use to me.

My question, really, is what am I missing/doing wrong?

And is anyone else experiencing the same thing?

---

### Post by Ilalmi on 2009-11-14
GRUB Legacy had to be replaced, because it has become unmaintainable ([http://www.gnu.org/software/grub/grub-2-faq.en.html](http://www.gnu.org/software/grub/grub-2-faq.en.html)). 
You can find a feature overview on [http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

I have to wait for the GRUB menu for some seconds, too. On my system the reason seems to be that I have installed GRUB2 and Linux on different disks ([http://ubuntuforums.org/showthread.php?t=1319183]("http://newyork.ubuntuforums.org/showthread.php?t=1319183")).

Be patient :-) GRUB2 seems to be still in the fledging stages.

---

