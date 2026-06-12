---
title: "x won't start; goes to CLI login"
date: 2011-11-16
forum: General Help
---

### Post by jynyl on 2011-11-16
This was a fresh install of Kubuntu 11.10 64bit back in October, and updates up to date since then.
Today, on startup, it briefly showed blue screen with "Kubuntu", then went to black screen with command line log in.  It appears that x doesn't start at all.  Startup on recovery mode (from grub) gives same result.

How can I troubleshoot / correct this?

TIA

Peter

---

### Post by qualicum on 2011-11-16
For a black screen after selection from grub2 menu, you might look at this article;
[http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html](http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html)
  Several possibilities also exist, such as; a malconfigured "splash screen" bitmap at the login screen; If you have a ram chip with meager compatibility for your motherboard, its a possibility to disable "suspend to ram" option in your BIOS setup configuration option for Power Management; lastly, although you haven't so indicated a message such as 'Marking TSC... bad/error' condition for cpu frequency/power conservation... Which to fix, you must edit grub.conf to change from one type of clock to another; reference that by googling the phrase "Marking TSC bad" to link to....no never mind, I found my link to it, which is here;
[http://ubuntuforums.org/showthread.php?t=1587276](http://ubuntuforums.org/showthread.php?t=1587276)

 A safe way to start troubleshooting is to put in the install DVD and when it boots, select the rescue option, at least you can re-install the grub2 boot loader if it has failed.
Good luck

---

### Post by jynyl on 2011-11-16
thanks for your help

I tried rebooting again, selecting the recovery mode option in grub.  Previous times this just gave black screen with CLI login, but this time it went on to KDE login.  The system logged in ok, but amarok ran at 100% of a cpu.  Then shutdown went ok, and normal reboot.

Maybe a transient hardware problem.  Time to backup my data.  The box is only about 3 years old, so it shouldn't be packing up yet!

---

### Post by raja.genupula on 2011-11-16
> **jynyl said:**
> thanks for your help

I tried rebooting again, selecting the recovery mode option in grub.  Previous times this just gave black screen with CLI login, but this time it went on to KDE login.  The system logged in ok, but amarok ran at 100% of a cpu.  Then shutdown went ok, and normal reboot.

Maybe a transient hardware problem.  Time to backup my data.  The box is only about 3 years old, so it shouldn't be packing up yet!

Hi man  , is your system is enough good with the requirements of Kubuntu ? 
[http://en.wikipedia.org/wiki/Kubuntu#System_requirements](http://en.wikipedia.org/wiki/Kubuntu#System_requirements)

---

### Post by jynyl on 2011-11-17
> **raja.genupula said:**
> Hi man  , is your system is enough good with the requirements of Kubuntu ? 
[http://en.wikipedia.org/wiki/Kubuntu#System_requirements](http://en.wikipedia.org/wiki/Kubuntu#System_requirements)

I hope it is enough;
CPU: Intel Core2 Quad Q9440S 2.66GHz
RAM: 4GB DDR3
Disk: 1TB SATA2
Graphics: GeForce 9800GT 1GB DDR3

---

