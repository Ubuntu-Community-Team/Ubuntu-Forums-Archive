---
title: "Driver Problems!"
date: 2011-04-15
forum: General Help
---

### Post by Allanss on 2011-04-15
I have a Compaq Presario 700 that i have recently installed ubuntu 10.10 Maveric. Previously i had Kubuntu 9.4 Jaunty downloaded and it worked fine. Now, after installing, ever time it boots i am given the error:

vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1

This wouldnt allow me except, one it slows down my incredible boot speed, and 2 my Xserver crashes anytime a screensaver comes on or wine i ran. obviously the second matter is much more weighty. The problem maybe more widespread, but i have a limited amount of installed applications because i installed 10.10 recently. I recon this problem is due graphics card because others have had graphics card problems with the screensavers and wine and when the xserver crashes, large distorted icons and letters are shown. i believe one was the firefox logo. I am not sure whether these problem are related, but i found someone referencing nvidia graphics card with nvidia mbus. Im not sure if nvidia drivers are appropriate for my system. 
Any help gretly appreciated!!!

Thanks,
Allan

---

### Post by sanguinoso on 2011-04-15
To determine your graphics card, you can type ```
sudo lshw -C display
```

Then please post the output here.

---

### Post by Allanss on 2011-04-15
*-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=255 mingnt=4
       resources: memory:e8100000-e817ffff memory:f0000000-f7ffffff memory:e8180000-e818ffff

thats what i got

---

