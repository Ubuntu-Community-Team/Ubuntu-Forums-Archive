---
title: "Cant install 12.04 in an alienware aurora R4"
date: 2012-04-28
forum: General Help
---

### Post by Lancro on 2012-04-28
I put the usb, it boots, it let me choose between install ubuntu or try without installing, and then a blank screen, no ubuntu splash screen or something similar, It boots on uefi, Im leaving the technical specifications if it can help, I didnt have any problems in 2 years with my others computers...

Processor: Intel core i7-3930K (Six core, 12 MB cache) overcloaked up to 3.9 Ghz
Memory: 8192 MB (4x2GB) 1600 MHz DDR3 Quad Channel
Hard Drive: 1TB SATA 6Gb/s (7200 RPM) 32MB Cache
Graphics: 1GB GDDR5 NVIDIA GeForce GTX 555

Thanks for the help.

---

### Post by Lancro on 2012-04-28
I have been studing the issue, maybe nomodeset could help me, but when I boot my usb, theres no F6 option or purple screen, just text mode with try ubuntu, install ubuntu or boot commands, any ideas on how can I do the nomodeset option?

Thanks.

---

### Post by jcperezma on 2012-05-04
Have you succeeded?

---

### Post by tynaud on 2012-05-05
Hi there

I am having issues with an aurora r4 too (2x less ram for me)...
I cannot boot on live cd nor usb live key in uefi mode (it directly boot on win7), it works only in legacy... How did you manage this ? Did you change something in bios ? How did you set your usb key (I tried unetbootin and used a 10.04 install too... same result.) And in the bios in peripheric priority, i can see usb disk and hdd, but the cd/dvd appears only in legacy mode... strange... Even using the boot device menu (F12) and selecting the USBkey is starting win7. 
I am considering reinstalling win7 an ubuntu in legacy mode for now... More of this, I have 17 computers like this one, and plan to use clonezilla to deploy ubuntu. I have doubt about this cause of EFI partition... Sounds like UEFI will make our live harder :P
Here is the link of my bootinfo if it can help (usb livekey and liveCD at the same time, don't know which one is currently used :))  :
[http://paste.ubuntu.com/968712/](http://paste.ubuntu.com/968712/)


Thanks

---

### Post by manuhalo on 2012-07-24
> **Lancro said:**
> I put the usb, it boots, it let me choose between install ubuntu or try without installing, and then a blank screen, no ubuntu splash screen or something similar, It boots on uefi, Im leaving the technical specifications if it can help, I didnt have any problems in 2 years with my others computers...

Processor: Intel core i7-3930K (Six core, 12 MB cache) overcloaked up to 3.9 Ghz
Memory: 8192 MB (4x2GB) 1600 MHz DDR3 Quad Channel
Hard Drive: 1TB SATA 6Gb/s (7200 RPM) 32MB Cache
Graphics: 1GB GDDR5 NVIDIA GeForce GTX 555

Thanks for the help.


Hi, I'm having the same problem with my newly bought Aurora R4. Both the live CD trial and the direct installation result in a  blank screen and nothing else happening, forcing me to reboot. Has anyone found a solution yet?

---

### Post by manuhalo on 2012-07-30
Solved the problem by forcing the ```
nomodeset
``` option at boot from the live cd; you can disable it after installing the proprietary driver (nvidia-current in my case). The only problem is that at boot I don't get any grub text, just the purple background, and the only way to boot into Windows (I went for a dual-boot system) is to select Boot options at the bios screen, which then allows me to select one of the UEFI options. Ugly, but it gets the job done.

---

