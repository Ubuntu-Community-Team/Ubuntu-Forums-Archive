---
title: "System doesn't stay shutdown"
date: 2010-11-27
forum: General Help
---

### Post by ScottTParker on 2010-11-27
When I shut down the computer, it does not remain shut down.  This is different from "restarting" the computer because when I "shutdown" the computer powers down, the fan and disks stop spinning for a second, and then everything starts again.  When I "restart" the fan and disks remain spinning throughout the restart process.
Further, the computer is dual booting with Windows XP Pro.  If I shut down from Windows, the system remains shut down.

System Information:
Ubuntu 10.04 Lucid Lynx
kernel: 2.6.32-26-generic
Computer: Dell Optiplex GX270
Bios Version: A07

I have tried the following commands and they all result in a reboot:
poweroff
shutdown
halt

---

### Post by dcstar on 2010-11-27
> **ScottTParker said:**
> When I shut down the computer, it does not remain shut down.  This is different from "restarting" the computer because when I "shutdown" the computer powers down, the fan and disks stop spinning for a second, and then everything starts again.  When I "restart" the fan and disks remain spinning throughout the restart process.
Further, the computer is dual booting with Windows XP Pro.  If I shut down from Windows, the system remains shut down.

System Information:
Ubuntu 10.04 Lucid Lynx
kernel: 2.6.32-26-generic
Computer: Dell Optiplex GX270
Bios Version: A07

I have tried the following commands and they all result in a reboot:
poweroff
shutdown
halt

Try resetting the BIOS to defaults.

---

### Post by WorMzy on 2010-11-27
Ubuntu cannot make the system power on. If such a thing is happening, it is happening because of settings in the BIOS, not in Ubuntu.

---

### Post by iNsOmNiOuS on 2010-11-27
How long does everything stay running one you have "shutdown" or does it just continue permanently ?

---

### Post by ScottTParker on 2010-11-27
In regards to the BIOS issue:
There is no option to reset the BIOS settings to default.  The following settings are the ones I would expect would be most pertinent to this problem, but their values seem to suggest that the computer should remain shut down:

Auto Power On: Disabled
Remote Wake Up: Off
Fast Boot: Off

If there are other typical problematic settings please let me know what they typically would be called.

Further, I doubt it is exactly a BIOS issue because if it were, then I would expect the computer to restart when shut down from Windows, which it does not.  Additionally this problem did not occur until I upgraded from Jaunty.  Perhaps Ubuntu is not sending the computer into the proper Sleep/Hibernate/Shutdown state


In regards to the running "shutdown now":
the computer just runs indefinitely on the splash scren, although it seems to stop at different spots on the splash screen on different shutdowns.

---

### Post by ScottTParker on 2010-12-16
Digging a further, I have found that when I use
```
sudo shutdown -p now
```the computer shuts down fine, and then reboots after staying off for ~1 sec.  This is the same behavior as going to the power-button-type menu and selecting "shut down". 
However, if I use 
```
sudo shutdown now
```or
```
sudo shutdown -h now
```the system hangs.  Escaping (Esc or F1) out of the spash screen first gives me the folloing "Recovery Menu":
  -resume
  -clean
  -dpkg
  -failsafex
  -grub
  -netroot
  -root
I usually select "resume" at which point the computer appears to try to boot up again and hangs on the entry "Checking Battery State     [OK]"
Tapping the power button then shuts the computer down for a moment, and then it boots up like normal.  
Investigating this, I have found that this is often a problem due to ACPI or Advanced Power Managment (ala [http://www.brighthub.com/computing/linux/articles/39504.aspx](http://www.brighthub.com/computing/linux/articles/39504.aspx)).  I have tried turning these off in the kernel options, at which point the computer gets stuck in the boot process (where it gets stuck depends on which options I use).

While I am not sure if these 2 problems (hanging on shutdown/not staying shut down) are related, it has got me asking: is Ubuntu having dificulties with the advanced power features, and therefore not shutting down properly?

---

### Post by ScottTParker on 2011-04-18
So after not making much headway in a few months, I have some new revelations.  The problem seems to be related to either the graphics card (nvidia GeForce 8400 GS) or the PCI slot into which it's plugged.  (I suspect that it is actually the graphics card because it is actually plugged into a port multiplier, and adding or removing the port multiplier without the card doesn't do anything).  So here's the additional symptoms:
1) If I shut down in Ubuntu with the card installed -> The computer restarts as described in the original post.
2) If I shut down in Windows with the card installed -> The computer shuts down.
3) If I shut down in Ubuntu or Windows and the card is NOT installed -> The computer shuts down.  But if the last OS to shut down the computer was Ubuntu, and then I plug in the graphics card while the computer is shut down, the computer IMMEDIATELY turns on again. (i.e. if I shut down in windows, remove the graphics card, start up in Ubuntu, shut down, and then plug in the card, it turns on)

I'm thinking this has something to do with Linux not turning off the PCI port, maybe an ACPI issue, but have no idea how to resolve it.

I should add that this behavior occurs, regardless if I use the standard Ubuntu drivers or the current nvidia drivers.

---

