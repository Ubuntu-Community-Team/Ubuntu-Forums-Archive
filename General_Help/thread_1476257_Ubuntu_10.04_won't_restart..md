---
title: "Ubuntu 10.04 won't restart."
date: 2010-05-07
forum: General Help
---

### Post by TheNerdAL on 2010-05-07
Sometimes, when I restart, Ubuntu 10.04 doesn't. My monitor just goes to sleep and I end up having to turn off the computer manually and turn it back on. 

Help! 

Thanks.

---

### Post by smiller24 on 2010-05-07
I'm running in to the same issue.  I walk away from the PC.  When I come back the Monitor is Black.  I have to reboot.  It seems to have something to do with the PC being Idle.  I don't have the power management set in my Screen saver set to shut off anything.

---

### Post by swalker23 on 2010-05-07
I'm having the same problem and also alot of other people.  Only solution so far is to open a terminal or create quick launch icon with the commands: 

To reboot
> sudo shutdown -r now

To shutdown
> sudo shutdown -h now

---

### Post by smiller24 on 2010-05-08
I found a work around of a sorts.  Its called 'Caffeine'.  I stops the screen saver from engaging and keeps the disks from going to sleep for a max of 186 hours.  You can find the installation instructions here:

[http://ubuntuforums.org/showthread.php?t=1473621](http://ubuntuforums.org/showthread.php?t=1473621)

To use and configure is easy:

1.) from Applications/Accessories select 'Caffeine.'
2.) Look in the Toolbar and you will see a coffee cup icon.
3.) Right-click and you can either:
    A.) Set the time that Caffeine is active for
    B.) under 'Preferences' Select to have Caffeine run at startup and select a specific process you want it tied to that will force Caffeine to stay turned on for.  In my case I used wpa_supplicant as it is always running.  Therefore it keep Caffeine Running.

I think this should get Ubuntu Users who are running in to this problem through the current crisis until a permanent fixed is found.  So far it has worked.  Before I was rebooting like 5 to 6 times per day.  I left the PC running all night and everything was running still in the morning.

If someone comes up with something better let me know.  Good luck.

---

### Post by TheNerdAL on 2010-05-09
> **swalker23 said:**
> I'm having the same problem and also alot of other people.  Only solution so far is to open a terminal or create quick launch icon with the commands: 

To reboot


To shutdown

Sometimes those don't work.

---

### Post by smiller24 on 2010-05-09
Well.  Just a thought.  But, still.  I'm 48 hours going on 72 and not shut down disks or reboots.  Hopefully Ubuntu will figure this out.  As I've pretty much narrowed down that the disks are going to sleep after the screen saver shuts off the monitor.

If you run across anything else let me know.

Cheers!

---

### Post by Catharsis on 2010-05-09
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by smiller24 on 2010-05-09
Intel graphics card.  I'm sure its one of the affected ones that have been an issue since 9.04.  I've applied the fixes that have been mentioned in this page here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes).  No dice.  There is some moderate improvement.  But not a lot.  The Caffeine app seems to be a work around at best.  But so far the only one that prevents me from having to reboot.

Here is the answer to your question though:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

If you have any better suggestions I am definitely open to the them.  Though I will say that adding the 'Versa' driver to the xorg.conf was darn near disastrous.  Fortunately Ubuntu pulled out the backed up file of my drive and put it to the way it was.  So I would say stay away from that one.

Thanks.

---

### Post by Catharsis on 2010-05-09
If i915.modeset=1 didn't work for you, you can try i915.modeset=0 instead. This fixed graphics problems for some other intel users.

---

### Post by TheNerdAL on 2010-05-09
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```
I use the nVidia one.

---

### Post by timjohn7 on 2010-05-09
Same problem, same video card on a Fujitsu Siemens P4 Laptop.  I've had plenty of other video issues under previous releases, all of which are solved under 10.04, but this black screen without waking is new and very irritating.  I also haven't been able to pin down any specific timeframe when it activates.

---

### Post by Catharsis on 2010-05-09
> **TheNerdAL said:**
> ```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```
I use the nVidia one.

Try booting with "nomodeset".
1) Hold down Shift as you boot to enter grub.
2) Press 'e' to edit. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to reboot.

---

### Post by TheNerdAL on 2010-05-10
> **Catharsis said:**
> Try booting with "nomodeset".
1) Hold down Shift as you boot to enter grub.
2) Press 'e' to edit. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to reboot.

Thanks, that works! :)

---

### Post by Catharsis on 2010-05-10
Glad to hear it. Make sure your nVidia driver is activated in System->Administration->Hardware Drivers.

If the nVidia driver doesn't fix the issue, you can make nomodeset permanent by editing /etc/default/grub. Change the line below so it reads:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

---

