---
title: "laptop gets hot running ubuntu"
date: 2009-12-28
forum: General Help
---

### Post by autogun on 2009-12-28
Howdy all,

I've a brand new HP Pavilion dv6 1340ej which is currently running on dual boot with Ubuntu and Windows 7.

When Im working for about an hour with Ubuntu, my laptop gets very hot - This is kind of stopping me from using Ubuntu since Im afraid something bad can happen to my laptop.

On the other hand, I can work hours on hours with Windows 7 and laptop's temp remains normal.

Can somebody suggest something?

Best regards,
Danny

---

### Post by mörgæs on 2009-12-28
Does it also run hot with Ubuntu 8.10 or 9.04 on a live CD?

---

### Post by pluto4ps on 2009-12-28
Check in Power Management whether the option "Spin Down Hard Disks when possible" is Unchecked. If is checked then your Laptop may generate more heat....

---

### Post by cartisdm on 2009-12-28
You can install this to monitor your system

```
sudo apt-get install sensor-applet
```

You may also want to look into this fan control guide created in another thread:

[HOWTO: Fancontrol]("http://ubuntuforums.org/showthread.php?t=42737")

---

### Post by autogun on 2010-01-02
mörgæs - I've been using LiveCD for over a hour and it didnt get as hot as it gets when using Ubuntu for 10min

pluto4ps - The option is unchecked.

cartisdm - Seems like I cant install it, no package found.

Please suggest,
I'd love to use Ubuntu as main OS.

---

### Post by derekmbarnes on 2010-01-03
> **pluto4ps said:**
> Check in Power Management whether the option "Spin Down Hard Disks when possible" is Unchecked. If is checked then your Laptop may generate more heat....

How much heat are we talking about? Could it noticeably affect the temperature of the CPU?

-----

autogun: I recommend installing GKrellM from the Software Center to monitor your system via GUI; F1 opens app configuration. If it doesn't see your CPU temperature sensor, open Terminal and run

```
sudo apt-get install acpi
```

Your CPU option should show up after that. This is important; a lot of us have been having problems with this distro where the fan for the CPU won't turn on until the temperature reaches about 200 degrees Farenheit. (We're still working on the problem...thread: [http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161) )

---

### Post by mörgæs on 2010-01-04
> **autogun said:**
> mörgæs - I've been using LiveCD for over a hour and it didnt get as hot as it gets when using Ubuntu for 10min

...

Please suggest,
I'd love to use Ubuntu as main OS.

Then I guess that a short-time solution could be installing the version, you tried on the live CD.

---

### Post by kwpowers on 2010-01-04
I have a pavilion that used to run hot.  It ran hot and the power supply box ran hot.  the issue was hardware, specifically ram. Linux did not report the correct ram for the hardware configuration.  use the live cd to do a memtest and verify it is not a hardware problem.  I had to send my computer back for repair.  Since then my computer has been running 20 to 30 degrees cooler

---

### Post by Groundswell on 2010-01-04
what i've noticed specific to me is that with stuff like desktop effects enabled, graphics cards and what not are going to run warmer than they would sitting on desktop in XP, or even Win7. In ubuntu they idle at 50c, where as in windows it would be about 35-40c.
This may also be a factor in your heat problem.

---

### Post by autogun on 2010-01-04
> **mörgæs said:**
> Then I guess that a short-time solution could be installing the version, you tried on the live CD.

I've installed the same version I've been running LiveCD from.
```
Linux danny-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

```

> **derekmbarnes said:**
> autogun: I recommend installing GKrellM from the Software Center to monitor your system via GUI; F1 opens app configuration. If it doesn't see your CPU temperature sensor, open Terminal and run

```
sudo apt-get install acpi
```

Your CPU option should show up after that. This is important; a lot of us have been having problems with this distro where the fan for the CPU won't turn on until the temperature reaches about 200 degrees Farenheit. (We're still working on the problem...thread: [http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161) )
[IMG]http://img695.imageshack.us/img695/6099/78079404.png[/IMG]
Here's a screenshot from GKrellM I've installed,

What can you tell from the above screenshot?

---

### Post by mörgæs on 2010-01-05
If you right-click on the top of the application ('danny-laptop'), you will see the options for configuring Gkrellm. Here you can add the thermometer, which is not enabled in the screen shot.

---

### Post by autogun on 2010-01-05
mörgæs - Thank you very much for trying to help me!

[IMG]http://img80.imageshack.us/img80/8685/ss2f.png[/IMG]

The temp is always between 48C-50C.. 

This is really weird since I cant even touch the upper left side of my laptop's bottom with my had since its so hot...

---

### Post by mörgæs on 2010-01-05
Yes, unfortunately there are some bugs in 9.10 regarding overheating and/or the fan not running fast enough. That's why I suggested trying an older version of Ubuntu.

I just came across this:
[http://ubuntuforums.org/showthread.php?t=1372890](http://ubuntuforums.org/showthread.php?t=1372890)
Maybe it can help? Just a guess, I have not tried myself.

---

### Post by autogun on 2010-01-06
Unfortunetly, mörgæs, I couldn't fine anything related to AHCI in my laptop's bios..

Thanks for the help,
Would like to hear more suggestions.

---

### Post by autogun on 2010-01-09
Bump

---

### Post by mexlinux on 2010-05-10
Could it be this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156)

---

### Post by finlost on 2010-05-10
My dual boot laptop definitely runs hotter running Ubuntu than Windows.  I assumed it was due to the amount of pr0n we watch while running Ubuntu.  :)

---

### Post by autogun on 2010-05-23
Here I am, 6 month later, back to report that I can happily use my Ubuntu 10.04 (Lucid Lynx) now since problem has been solved for my HP Pavilion dv6 1340ej by installing ATI drivers (using System > Administration > Hardware drivers > ATI/AMD proprietary FGLRX graphics driver).

:guitar:

---

