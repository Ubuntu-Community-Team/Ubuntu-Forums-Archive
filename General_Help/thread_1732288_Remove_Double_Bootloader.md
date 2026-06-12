---
title: "Remove Double Bootloader"
date: 2011-04-18
forum: General Help
---

### Post by Shooz136 on 2011-04-18
I'm using a Wubi install of Ubuntu inside of Windows 7, and currently the computer boots to the Windows Bootloader, and when I choose Ubuntu, it boots Grub, where I have to choose Ubuntu again.  Is there any way to simply use GRUB to replace the windows bootloader?  I didn't know if that was possible while using Wubi?

Thanks,
Shooz136

---

### Post by Karlchen on 2011-04-18
Hello, Shooz136.

As long as you are running Ubuntu using Wubi there is no way around it. (To the best of my knowledge.)

Kind regards,
Karl

---

### Post by Rubi1200 on 2011-04-18
Hi and welcome to the forums :-)

In a word, no. Wubi needs to use the Windows bootloader, after which it can then hand off to GRUB. In part, this has to do with the fact that it uses a virtual file-system placed within the host system. If you were to try and install GRUB to the MBR in this situation you would likely find both Windows and Ubuntu unbootable.

It is also inadvisable to attempt to use boot manager software to change this, as the result will essentially be the same; an unbootable system.

If you want to clean up the GRUB menu a bit, you can use Grub Customizer:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Shooz136 on 2011-04-18
Thanks for your quick replies everyone - I figured that was the case with WUBI.

---

### Post by mike555 on 2011-04-18
You can set the time displayed to " 0 " ,then you still use grub , but you don't see it ...........

---

### Post by bcbc on 2011-04-18
> **mike555 said:**
> You can set the time displayed to " 0 " ,then you still use grub , but you don't see it ...........

Grub2 won't honour that if it detects multiple OSes. (Unless something has changed recently). There is a way around that by manually editing a grub script. But I don't recommend it. For the inconvenience of hitting down arrow, enter, enter... it seems a lot of effort and not worth the risk.

You can change the default OS to boot in Windows so that it goes to Ubuntu instead of Windows - and you can reduce the timeouts to something more reasonable - but DO NOT set the timeout in Windows to 0 or Windows will not boot anymore. 

That's about the best you can do with Wubi. If you find you are always booting Ubuntu, you might want to consider migrating to a traditional dual boot.

---

