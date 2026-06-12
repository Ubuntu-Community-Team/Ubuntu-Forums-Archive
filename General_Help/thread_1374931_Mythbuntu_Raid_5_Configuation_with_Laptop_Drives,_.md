---
title: "Mythbuntu Raid 5 Configuation with Laptop Drives, Possible?"
date: 2010-01-07
forum: General Help
---

### Post by diskmaster23 on 2010-01-07
After trying to get my mdadm software raid working, I have finally decided to ask the Cloud to see if my setup is even possible.

I wanted to setup a RAID 5 setup with 4 Western Digital Scorpio Blue WD2500BEVT 250GB 5400 RPM 2.5" SATA 3.0Gb/s Internal Notebook Hard Drives and using the Rosewill Silicon Image RC-209-EX PCI (which uses the Silicon 3114 chip). I know that this is not a true hardware raid setup. I knew that before buying this equipment. 

At first I was not able to get the software raid to work. The drives kept having buffer I/O problems. One of the drives, I knew for sure was done, but I even tried to do raid 5 with only three drives and kept running into the same problem. 

My question is, theoretically, should I even be doing a RAID setup with these laptop drives? Should I even be doing a RAID setup at all? It seems like once I think I get it all going, it just comes up with another buffer i/o problem. 

As I speak, I am running the Extended test with the WD Diagnostic Software on the drive that posted the most recent buffer i/o problem. Just some 12 hours ago I did the exact same extended test on all the drives and it came up clean.

Anybody else have experience with this? Have any recommendations or questions?

Machine Specs:
[LIST]
[*]1x AMD Athlon 64 3000+ Winchester 1.8GHz Socket 939 Processor
[*]1x GIGABYTE GA-K8NS Ultra-939 939 NVIDIA nForce3 Ultra ATX
[*]1x KINGMAX SuperRAM 512MB (2 x 256MB) 184-Pin DDR SDRAM DDR 400
[*]2x Kingston ValueRAM 1GB 184-Pin DDR SDRAM DDR 333 
[*] 1x Hauppauge Tuner Card 1045 PCI
[*] 2x SNT SNT-SATA2221B Dual 2.5" SATA SSD / HDD to 3.5" Bay Trayless Hot Swap
[*] 5x Western Digital Scorpio Blue WD2500BEVT 250GB 5400 RPM 2.5" SATA (One drive on RMA, only 4 were supposed to be used in the RAID configuration)
[*] 1x Rosewill Silicon Image RC-209-EX PCI
[/LIST]

OS:
Mythbuntu 9.04

---

### Post by Fcon_Vpro on 2010-01-10
1st answer: Yes you can run raid on these drives without issues. Ive run raid5 on USB external drives before without problems.
2nd answer: If you dont want to lose data then you should definetly be running raid. raid5 or raid6 should be your only options as raid1 just isnt worth it.

Your hardware should run raid without any problems. 

It is a bit weird that you are getting these I/O errors. 
Have you tried using your motherboard sata controller instead? Perhaps the Rosewill card is faulty.

---

### Post by diskmaster23 on 2010-01-10
> **Fcon_Vpro said:**
> 1st answer: Yes you can run raid on these drives without issues. Ive run raid5 on USB external drives before without problems.
2nd answer: If you dont want to lose data then you should definetly be running raid. raid5 or raid6 should be your only options as raid1 just isnt worth it.

Your hardware should run raid without any problems. 

It is a bit weird that you are getting these I/O errors. 
Have you tried using your motherboard sata controller instead? Perhaps the Rosewill card is faulty.

Thanks for responding.

I was finally able to get the RAID 5 up and running, but I had to RMA two of the five brand new Western Digital drives. I kept running into intermittent drive issues with another one of the drives. 

I just hope one more drive does not fail because then I will loose all the data. <crosses fingers>

For those that are thinking about running a software RAID 5 setup, I recommend updating your hardware. While my system operates just fine, nothing beats having proper hardware. It may be more expensive, but in the long run it runs much better. Just my two cents

---

### Post by Fcon_Vpro on 2010-01-10
Its always a good idea to test out your new raid system before copying all your data onto it. Once your system is up and running, give it a couple weeks to test before relying on it full time.

I disagree about the updating hardware bit for running a software raid5 setup. Your system you mentioned above would run it perfectly. 
However, as a mythbuntu system, I can understand the hardware update stuff, especially if you plan on playing 10GB 1080p mkv files, etc

Hope once the drives arrive back for you that everything will go well.

---

