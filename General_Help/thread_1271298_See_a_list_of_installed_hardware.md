---
title: "See a list of installed hardware"
date: 2009-09-20
forum: General Help
---

### Post by simartem on 2009-09-20
Hi,
I am very new to Ubuntu. I have installed Ubuntu 9.0.4 as a second OS on my secondary HDD. I can boot into Ubuntu easily.. Everything seems to work fine. My question is, how can i see a list of my hardware detected by Ubuntu, if the hardwares are detected as desired. Which drivers are installed for the detected hardware. How can i see a list of my installed hardware/drivers ? I have an ATI Radeon IGP 9100 embedded graphics card in my Asus P4R800-VM mainboard, i want to know if its detected with the correct name/model. Thank you in advance. "Ubuntu for humans!"

---

### Post by jmszr on 2009-09-20
simartem,

This will give you a fairly detailed list of your hardware:```
 sudo lshw -html > ~/Desktop/hardware.html
```

The list will show up on your Desktop.

---

### Post by simartem on 2009-09-20
thank you jmszr, greatly appreciated.

---

### Post by benerivo on 2009-09-20
You could try```
lspci
```to get a concise list of hardware, or```
lspci -v
```to get a verbose list, with driver information.

---

### Post by simartem on 2009-09-20
Thank you benerivo.
My display driver is explained like the following in the report, i think there is no need for me to update the driver or take any action for the graphics card because the name seems correct. Do i need to make any update for this hardware ?

id:[COLOR=gray]display[/COLOR]
                   description: VGA compatible controller                 product: Radeon 9100 IGP                 vendor: ATI Technologies Inc                 physical id: 5
                 bus info: pci@0000:01:05.0
                 version: 00                 width: 32 bits                 clock: 66MHz                 capabilities: agp agp-3.0 pm bus_master vga_palette cap_list                 configuration: latency=64 mingnt=8

---

### Post by benerivo on 2009-09-20
Well the hardware detection is fine. I know ubuntu supplies a way to install specialist drivers for ATI and NVIDIA cards. I'm not on my ubuntu machine at the moment (and i don't have an ati or nvidia card) so i can't say much more, but check this...

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

You might have already done this from the options provided in the main menu.

---

### Post by simartem on 2009-09-20
Dear benerivo,

I appreciate your help. With best regards.

---

### Post by UpsideDownFace on 2009-09-20
The way I get drivers for nvidia and other restricted devices is to go into Synaptic Package Manager > Settings > Repositories and tick the box "Software restricted by copyright....(multiverse)"

Then eventually you will be offered drivers for downloading.
A coloured symbol appears in the top panel, near the "logout" symbol and you have to click it.
I am sorry not to be more specific, but I have done it several times without any trouble, so I haven't recorded exactly what I did.

---

### Post by UpsideDownFace on 2009-09-20
The way I get drivers for nvidia and other restricted devices is to go into Synaptic Package Manager > Settings > Repositories and tick the box "Software restricted by copyright....(multiverse)"

Then eventually you will be offered drivers for downloading.
A coloured symbol appears in the top panel, near the "logout" symbol and you have to click it.
I am sorry not to be more specific, but I have done it several times without any trouble, so I haven't recorded exactly what I did.

---

### Post by gradinaruvasile on 2009-09-20
> **simartem said:**
> Thank you benerivo.
My display driver is explained like the following in the report, i think there is no need for me to update the driver or take any action for the graphics card because the name seems correct. Do i need to make any update for this hardware ?

id:[COLOR=gray]display[/COLOR]
                   description: VGA compatible controller                 product: Radeon 9100 IGP                 vendor: ATI Technologies Inc                 physical id: 5
                 bus info: pci@0000:01:05.0
                 version: 00                 width: 32 bits                 clock: 66MHz                 capabilities: agp agp-3.0 pm bus_master vga_palette cap_list                 configuration: latency=64 mingnt=8

Thats an ancient piece of hardware, it should be fully supported by the ubuntu included open source drivers.

---

### Post by UpsideDownFace on 2009-09-20
Sorry I sent a reply twice - it's showing my age or the time of night!

---

### Post by simartem on 2009-09-20
hi gradinaruvasile, you are right the hardware is ancient but Ubuntu still rocks with it :)
I am fully able to use compiz effects and its enough for the moment to learn and experience Ubuntu. I wish someday i will be installing Linux on a Quad-core system with a PCI-e 512 bit 1 GB graphics driver.. :) Its the first time i am meeting with Linux and it really feels so good.. Best wishes

---

### Post by simartem on 2009-09-20
> **UpsideDownFace said:**
> Sorry I sent a reply twice - it's showing my age or the time of night!

thank you very much upsidedownface.. I am very happy with your helps! Its late here too in Turkey.

---

### Post by gradinaruvasile on 2009-09-20
> **simartem said:**
> hi gradinaruvasile, you are right the hardware is ancient but Ubuntu still rocks with it :)
I am fully able to use compiz effects and its enough for the moment to learn and experience Ubuntu. I wish someday i will be installing Linux on a Quad-core system with a PCI-e 512 bit 1 GB graphics driver.. :) Its the first time i am meeting with Linux and it really feels so good.. Best wishes

There u have it... if compiz works well, no need for other drivers. U should set the video playback (press alt+f2 , type gstreamer-properties, go to the video tab) to x windowsystem (x11/etc) / Radeon texture device to have a smooth video playback (consider installing fusion-icon and disabling compiz when playing videos). I did that on a test system that had radeon 9100 or 9200 card (agp 4x, add on card) and got tear-free video playback. Also i tried that one with the alpha ubuntu 9.10 and compiz ran 2x faster.

---

### Post by simartem on 2009-09-20
nice tip gradinaruvasile.. I will try it..

Edit : Yes, the result is clearly better and faster and smoother.. How do you know these details :)

---

