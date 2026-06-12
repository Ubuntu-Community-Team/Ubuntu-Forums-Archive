---
title: "Triple Monitors - Dual Nvidia Cards - One heckuva frustrated user..."
date: 2012-03-06
forum: General Help
---

### Post by Roasted on 2012-03-06
Nvidia GT 430 PCIE
Nvidia 6200 PCI

Ubuntu 11.10
Gnome Shell

17" 1280x1024
24" 1920x1080
19" 1400x900

The best I can get is twinview, which I've had for years. The second I add another X session and tag in the other monitor and reboot, things are just... bad... just downright unusable. I'm not sure what I'm doing wrong.

Can anybody tell me the exact process in getting triple monitors working? People were telling me oh yeah this is pretty easy with Intel or Nvidia cards, etc. Well, I have Nvidia, and it feels like I'm running ATI gear... ](*,)](*,)](*,)](*,)

---

### Post by dcstar on 2012-03-08
> **Roasted said:**
> Nvidia GT 430 PCIE
Nvidia 6200 PCI

Ubuntu 11.10
Gnome Shell

17" 1280x1024
24" 1920x1080
19" 1400x900

The best I can get is twinview, which I've had for years. The second I add another X session and tag in the other monitor and reboot, things are just... bad... just downright unusable. I'm not sure what I'm doing wrong.

Can anybody tell me the exact process in getting triple monitors working? People were telling me oh yeah this is pretty easy with Intel or Nvidia cards, etc. Well, I have Nvidia, and it feels like I'm running ATI gear... ](*,)](*,)](*,)](*,)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Roasted on 2012-03-09
I'm failing to see how that helps me. I have the driver installed. I just don't know what settings I need to alter within Nvidia-Settings to get triple monitor (dual gpu) working, or if it's not possible through the GUI, how I could edit Xorg to handle it accordingly...

---

### Post by haqking on 2012-03-09
for SLI you need to have the same GPU's, you have 2 different cards and for surround/3d vision which supports 3 monitors then as far as i know you need SLI

[http://sli.nvidia.com/page/slizone_faq.html#c16](http://sli.nvidia.com/page/slizone_faq.html#c16)

for ATI this would be crossfire.

Also you have different resolutions, which is likely to cause issues with nvidia SLI as it tends to cause stability issues and overheating as far as i know.

---

### Post by Roasted on 2012-03-09
I don't have SLI, I just have a graphics card in my PCIE slot and PCI slot and was hoping to somehow span the video feed across 3 monitors. Was I a bit too hopeful on the matter?

Like I said, GT 440 and 6200... I was hoping to run 2 off the 440 and a 3rd monitor off the 6200... :(

---

