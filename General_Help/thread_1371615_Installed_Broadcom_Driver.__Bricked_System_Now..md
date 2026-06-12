---
title: "Installed Broadcom Driver.  Bricked System Now."
date: 2010-01-03
forum: General Help
---

### Post by Roasted on 2010-01-03
Now, keep in mind - this is all from speculation since these systems have been formatted and worked around with since. But I'm posting this in hopes of people shedding light.

It started with my work laptop - a Dell Latitude E5500 with Kubuntu 9.10. I got a popup from hardware drivers saying there's a Broadcom driver available. B43 and STA came up. Well, B43 did nothing, so I install STA. It freezes halfway during the install but prompted a reboot. I reboot, come back in to Kubuntu, and all is well but it still says the STA driver was not installed. So, I got all of the latest updates from being wired to my network - including the .16 kernel. Now the STA driver works fine. Okay, all is well on my laptop. 

I'm in the Kubuntu IRC chat and someone was having similar issues. They did a fresh install and the Broadcom STA driver errored out similar to mine. The only difference was, when this person rebooted, she was unable to get into Kubuntu. No login screen whatsoever. So she went into recovery console, however, we weren't sure how to remove the Broadcom driver. As I type this she's already doing a fresh install to get around this issue. It's very frustrating having to use Windows-like troubleshooting techniques to fix Linux (by simply reinstalling). I'm hoping somebody can offer some insight here.

So I come asking several questions.

1 - What was it with the Broadcom STA driver on my laptop that didn't like the .14 kernel but .16 worked fine? Why didn't the .16 kernel work for this person trying the same STA driver with similar issues? 

2 - What was it with the STA driver for this other person that caused her login screen to just never appear and only get a black screen?

3 - How on earth do you uninstall a driver like this Broadcom STA driver from recovery console to get the system working again?

---

### Post by Gramps on 2010-01-03
```
apt-get purge bcmwl-kernal-source
```

Broadcom 802.11 Linux STA wireless driver source

These package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware.

---

### Post by BigCityCat on 2010-01-03
Look this up first cause I'm not an expert. As far as removing something command line. I think the command is

sudo apt-get --purge file name or application

never mind

---

### Post by Roasted on 2010-01-03
Thanks guys. Has anybody else had issues similar to this with broadcom drivers? I find it very poor to know that a driver can brick a system like this. :(

---

### Post by Roasted on 2010-01-03
New problem.

I just found a tutorial which said if I use jockey-text in terminal, it'll allow me via terminal to control the way the drivers in hardware manager act. So I typed jockey-text -l to list the drivers and it came back with mine. So I wanted to test disabling it and re-enabling it. I disabled it fine. When I re-enabled, my laptop locked up. I cut the power, rebooted, kernel panic. When I go into recovery console, I get the same thing.

I am honestly downright surprised how incredibly easy it is to brick a linux system. What can I possibly do to get this laptop rolling?

EDIT - Well, I ended up rebooting to the .16 kernel (the one kernel panicing) and I couldn't get it fired up. Dropped back to .14 and removed the driver via sudo apt-get remove bcmwl*. Then I re-added it and all was well. .16 kernel works fine with wifi again. I tried repeating my steps several times and nothing successfully repeated the kernel panic I had.

So the gizmo is working again, but now I'm unsure of something. When I go to hardware drivers, I can't remove the broadcom STA driver. Why is that? It's as if the remove button is just non responsive.

---

### Post by Roasted on 2010-01-17
Just wanted to update this thread.

I was screwing around with other distros for a few days here, so my original system had been wiped. openSUSE, Mandriva, blah blah. Anyway I'm back to Kubuntu. Gotta love the *buntu roots and even if KDE on Kubuntu isn't very customized, it's easy enough to get it flowing nicely.

Anyway, I fired up Kubuntu 9.10 and immediately updated, bringing down the new kernel. This was all done wired.

I reboot, go to hardware manager, and download the Broadcom STA driver, which directly supports the BCM4322 - which I have. As it downloads, my laptop freezes up 100%. I cut the power, and reboot. I boot back up, hit up hardware manager, and try to re-download the Broadcom STA driver. I got an error. I exit out of hardware manager, re-open it, and I re-download it. This time I successfully re-download it. However, when I went to reboot, I couldn't click anything. I was able to move the mouse, but nothing worked. So, I cut the power again. I boot back up, and blam I have wireless. Awesome.

I'm very happy I have wireless. My big question is, why did I have to jump through these hoops with the laptop locking up each time I did this? I didn't have these problems when I got the broadcom-wl driver from mandriva, opensuse, fedora, or any other distro. Why was it problematic for me?

---

