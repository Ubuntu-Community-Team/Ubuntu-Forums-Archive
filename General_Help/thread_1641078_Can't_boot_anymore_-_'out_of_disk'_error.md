---
title: "Can't boot anymore - 'out of disk' error"
date: 2010-12-08
forum: General Help
---

### Post by WA1DH on 2010-12-08
My file server has been running fine for the past several months, until today. I was experimenting with the power consumption of a different motherboard and CPU, so I removed the hard drive from the server and booted it in another system. All was fine until I put the drive back in the server and came to the Grub rescue prompt which stated "Error: out of disk" or something similar to that. Also, when booting, there is a splash screen for my RAID card. I don't use RAID, but have a 4-port PCI card since there is no onboard SATA on my server board. This splash screen used to list the hard drive and its size (1TB), but now says "0GB". This splash screen comes up before the grub rescue prompt appears.

I have connected the hard drive to another system and can mount/access everything on it. However, I cannot boot from it on any system. I can access the drive from a live CD and everything appears normal. I attempted a reinstall of Ubuntu on the / partition (leaving my /home partition intact) but this did not solve the problem.

I'm not sure why booting the HDD on another system made this problem, and I really need to correct it to get my server back running. I would like to avoid formatting the entire drive if at all possible. If there were a problem with the MBR or grub, wouldn't the reinstall of Ubuntu have corrected that? The drive itself is fine, as I checked the SMART data and it has no errors/bad sectors. I bought the drive new earlier this Spring.

Any help or suggestions greatly appreciated.

---

