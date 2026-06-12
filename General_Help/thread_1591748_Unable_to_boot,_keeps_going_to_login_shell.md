---
title: "Unable to boot, keeps going to login shell"
date: 2010-10-09
forum: General Help
---

### Post by oxf on 2010-10-09
Hi,

When I boot up it keeps taking me to a login terminal shell. I can login but am unable to resume a normal boot afterwards either. Whats going on?

I did run update manager yesterday which installed a kernel 2.6.32-25 but its happening with the previous version 2.6.32-24 as well. Recovery mode doesent seem to help either.
I booted from the live CD and ran fsck which reports "clean"

Any ideas of what's happening here and how to proceed?

Thanks...

---

### Post by Quackers on 2010-10-09
Does anything happen if you run startx from the terminal? Or try Ctrl+Alt+F7

---

### Post by oxf on 2010-10-09
> **Quackers said:**
> Does anything happen if you run startx from the terminal? Or try Ctrl+Alt+F7

Thanks for replying!
Ctrl+Alt+F7 does nothing.
startx does start the desktop though. But.... some of my applets in the top panel  are gone, like wireless and the shutdown is non functional.
I'm thinking I have a major problem here!

---

### Post by Quackers on 2010-10-09
If you can get to the desktop you can fix it. I suspect it is something to do with the video card driver. I'm afraid I don't know enough to help you any further but it may help somebody else to assist if you can post the details of your graphics card and the driver installed.

---

### Post by oxf on 2010-10-09
> **Quackers said:**
> If you can get to the desktop you can fix it. I suspect it is something to do with the video card driver. I'm afraid I don't know enough to help you any further but it may help somebody else to assist if you can post the details of your graphics card and the driver installed.

Well thanks for that anyway! at least I can get to the desktop...

FYI my graphics card is the ATI Radeon Express 200M

---

### Post by Quackers on 2010-10-09
You're welcome. 
At least you've got something pretty to look at while you're waiting :-)

Do you have the FGLRX driver loaded?

---

### Post by oxf on 2010-10-09
> **Quackers said:**
> You're welcome. 
At least you've got something pretty to look at while you're waiting :-)

Do you have the FGLRX driver loaded?

No I just have the default driver whatever that is, I cant remember
..

---

### Post by Quackers on 2010-10-09
Have you looked in System > Admin > Hardware Drivers? Is there a driver there? Is it activated?

---

### Post by oxf on 2010-10-10
> **Quackers said:**
> Have you looked in System > Admin > Hardware Drivers? Is there a driver there? Is it activated?

Yes there is a driver/activacted. Or at least there was until this problem erupted. Everything was fine until yesterday.

As of now though if I try to go to Sytem>Hardware Drivers I get this:

""org.freedesktop.DBus.Erroor.File:failed to connect to socket /var.run/dbus/system_bus_socket: no such file or directory"" 
Also Shutdown or other buttons don't work either.

Anyone have a sugestion where I should go from here??

---

### Post by coskierken on 2010-10-10
When an updated comes along, sometimes it will conflict with the video driver.  What I do is keep a copy in my root directory or where I know where it is so I can just go there.  I install it from a command line and everything will be normal.  Nvidia a famous for this, but I am not sure of ATI.  Give it a shot.  Hope this helps!

---

### Post by Gudrann on 2010-10-10
I seem to have the same problem, it started after I activated my Nvidia driver, I guess I can fix it by disabling it, but I can't seem to reach the desktop, startx doesn't work.

Can I disable the driver in the command line somehow?

G

EDIT:

I managed to boot in failsafe graphical mode. I disabled the nvidia driver, and afterwards was able to boot normally again.

---

### Post by oxf on 2010-10-10
> **coskierken said:**
> When an updated comes along, sometimes it will conflict with the video driver.  What I do is keep a copy in my root directory or where I know where it is so I can just go there.  I install it from a command line and everything will be normal.  Nvidia a famous for this, but I am not sure of ATI.  Give it a shot.  Hope this helps!

OK...possibly. I mean you may be correct. The only thing I would add is exactly the same problem occurs is select the previous kernel in Grub and boot from that which leads me to wonder if something has got seriously corrupted. I've booted from the Live CD and saved all my important stuff now fearing the worst!

---

### Post by aspiredfang on 2010-10-10
If the update you have done somehow clobbered the driver (I use an ATI card and every kernel upgrade, it has), I strongly recommend the following:

- Go in to your package manager; be it Synaptic, aptitude, etc.
- Remove and purge fglrx and anything that says ATI/radeon in the name
- Refresh your package list
- Install FGLRX afresh

This should configure your set up to work with the latest kernel and resolve the problem. It is a known bug that the security update in last patch...broke the AMD drivers. I'd personally use that approach but, for the proprietary drivers, AMD have released an actual fix that can be found 
@ [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

I hope this helps :)

---

### Post by oxf on 2010-10-10
> **aspiredfang said:**
> If the update you have done somehow clobbered the driver (I use an ATI card and every kernel upgrade, it has), I strongly recommend the following:

- Go in to your package manager; be it Synaptic, aptitude, etc.
- Remove and purge fglrx and anything that says ATI/radeon in the name
- Refresh your package list
- Install FGLRX afresh

This should configure your set up to work with the latest kernel and resolve the problem. It is a known bug that the security update in last patch...broke the AMD drivers. I'd personally use that approach but, for the proprietary drivers, AMD have released an actual fix that can be found 
@ [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

I hope this helps :)

OK many thanks for that!! :)
Previous kernel upgrades haven't been a problem ( maybe I've just been lucky with ATI drivers?) 

But good to know. I'll certainly try that and report back. 
Thanks!

---

### Post by oxf on 2010-10-11
> **oxf said:**
> OK many thanks for that!! :)
Previous kernel upgrades haven't been a problem ( maybe I've just been lucky with ATI drivers?) 

But good to know. I'll certainly try that and report back. 
Thanks!

OK the news is not good !  Thank god I have access to another PC!

I can't reinstall drivers as it appears my wireless is broken too. I tried launching it from the command line and it tell me wlan0 (and eth0 also) is not recognised which is  why the blue wifi light is not on.

Other functions don't work either, eg shut down button and Nautilus won't detect my flash drive.

I can't see anyway around this but to reinstall the system. If anyone can advise differently I'm all ears!

---

