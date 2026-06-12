---
title: "How to install my video card?"
date: 2010-04-26
forum: General Help
---

### Post by TurboThiago on 2010-04-26
Hi people,

I need some help to with my video card. I think it's not operating. It's a geforce 9500gt 1Gb 128bits. How can i see if it's working or not? And where can I find a driver to it? I've looked in the geforce's site and i've downloaded a file with the extension .run, but this file didn't work. What should i do?

my pc: Core2Quad, 4GBram, geforce 9500gt 1Gb 128bits, asus's motherboard, hd 500gb sata. Ubuntu 9.10 64bits

Thanks

PS: i'm from Brazil and my english is not so good. Sorry if i write something wrong.

---

### Post by cariboo on 2010-04-26
Just install the card, then go to System->Administration->Hardware Drivers, and enable the driver for your graphics device. Once installed and you have rebooted, go to System->Administration->NVIDIA X Server Settings to check out all the details.

---

### Post by mountlaurel on 2010-04-26
Just Install the video card in the motherboard and insert the drivers of the cd in the cd rom and install the video card driver. Then it will be work fine.

---

### Post by Serpher on 2010-04-26
Move the .run file into your home folder then press Alt + F2, log in, and execute the following commands:

```
sudo /etc/init.d/gdm stop
ls
sudo sh <Name of .run file, press TAB for autocomplete>
```

Then run through the installer.

---

### Post by TurboThiago on 2010-04-28
> Just install the card, then go to System->Administration->Hardware Drivers, and enable the driver for your graphics device. Once installed and you have rebooted, go to System->Administration->NVIDIA X Server Settings to check out all the details.

It worked. Thanks very much. There was two options. I'll try the two ones and choose the best for me.

> Just Install the video card in the motherboard and insert the drivers of the cd in the cd rom and install the video card driver. Then it will be work fine.

My cd driver doesn't have drivers to ubuntu. Just for windows and mac.

> Move the .run file into your home folder then press Alt + F2, log in, and execute the following commands:

 	Code:
 	sudo /etc/init.d/gdm stop
ls
sudo sh <Name of .run file, press TAB for autocomplete> 
Then run through the installer. 	

I could install by the cariboo907's hint. But i'll use your hint to install others things
Thanks to everybody.

Bye

---

### Post by 3rdalbum on 2010-04-28
> **TurboThiago said:**
> I could install by the cariboo907's hint. But i'll use your hint to install others things

Cariboo's post is the correct Ubuntu way to install the driver. The other thing about how to use that ".run" file is only applicable to the Nvidia driver and is not necessary for other sorts of files.

Always use the Hardware Drivers program method unless you have a pressing need not to.

---

### Post by TurboThiago on 2010-04-28
> Cariboo's post is the correct Ubuntu way to install the driver. The other thing about how to use that ".run" file is only applicable to the Nvidia driver and is not necessary for other sorts of files.

Always use the Hardware Drivers program method unless you have a pressing need not to.

OK 3rdalbum, i understand now. To install drivers and others aplications like this, I'll use hardware drivers. But if I can't i'll try the code way. I'm using the code way to configure my capture tv card and I am doing it slowly. Thanks 3rdalbum and thanks everybody.

bye

---

