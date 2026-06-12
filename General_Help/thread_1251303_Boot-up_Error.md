---
title: "Boot-up Error"
date: 2009-08-27
forum: General Help
---

### Post by attercop on 2009-08-27
I'm running Ubuntu 9.04 64-bit version. It boots and works all nicely. But at boot-up i get some errors that - after delaying boot for a few seconds - appear and disappear so fast that i can't note them down to do a Google search for a fix.

A couple of them appear slowly and are Softreset failed (device not ready) errors. But another one or more appears and it's about 4 lines long and says something about K8 and the BIOS.

Where can i find the logs for these error messages i'm getting on boot? Then maybe i can add an option to Grub and boot cleaner.

---

### Post by Lithium Rain on 2009-08-27
Explanation of how to obtain boot error logs here: [http://ubuntuforums.org/showthread.php?t=15158](http://ubuntuforums.org/showthread.php?t=15158)

Hope that helps =]

---

### Post by QIII on 2009-08-27
With regard to the "Softreset failed (device not ready) errors", I have noticed that I get as many "errors" as I have free SATA headers on my motherboard.

I am not sure at this point, but I believe that some combination of the way the BIOS and Ubuntu interact causes all the headers to be queried for a device, which means that a couple of them "fail".

It delays my start up by all of 1 second.

---

### Post by SuaSwe on 2009-08-27
I also get a couple of "not found" errors flashing up during boot. I think it's normal, to be honest. :)

---

