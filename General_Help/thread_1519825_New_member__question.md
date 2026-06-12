---
title: "New member  question"
date: 2010-06-28
forum: General Help
---

### Post by Ziton on 2010-06-28
Hi All
New here.
Been wanting to change to Linux for years.
[COLOR=#000000][FONT=arial]I'm building a new computer for home intertainment
Movies  Games TV. I'm not a hardcore gamer, mostly movies and internet. I hate  microsoft. 
I've installed Win95, 98, xp Hundreds of times.
My  first computer I was installing w95 once a week it seemed.Back in my  gaming days.
My new computer is an  
#  ASUS P5VDC-MX  motherboard
# Intel P4 2.8Ghz 800 1M CPU[/FONT][/COLOR][QUOTE]
 Western Digital Caviar Blue SE16 3.5in  320GB SATAII Internal Hard
[COLOR=#000000][FONT=arial] # Sony CRX320EE DVD/CD-RW  combo drive
# 350 watt ATX power supply with:
1 x SATA power lead
2GB   DDR2 PC4200 2x 1GB PC2-4200 533Mhz Dual Channel
I'm going to add a  Dual tuner HDTV FM card. Like Asus My Cinema PE9400 Combo PCI-E Tuner  Card or
Hauppauge WINTV-HVR-2250
What concerns me is the drivers  for graphic  ,sound cards ETC.
I'm looking at The Ubuntu Forum Community to get  started.
I have windows XP   [/FONT][/COLOR]I've  purchased the latest  version of of Linux XP Freespire &Ubuntu 2010. I'm planning  a dual  boot though I'd rather go FULL Linux only on the new computer in time. 
Thanks   for any suggestions or advice
Ziton

---

### Post by rollin on 2010-06-28
Just a suggestion but try the Ubuntu Live CD. Test the system when running to see what works with the drivers and stuff and what doesn't? Should be cool!
At least that way you can test your system and not worry about installation yet.

---

### Post by stderr on 2010-06-28
Hi Ziton, welcome!

Reinstalling the old Winblows versions over and over, yes, alas I also remember it all too well!

You'll find that most products can largely be configured to work in Linux; some are simpler to setup than in Winblows, some are definitely much harder, and a number cannot fully function correctly no matter how much configuring.

You might find the [Ubuntu Hardware Compatibility List]("http://ubuntuhcl.org/browse/categories") to be of assistance here. It's far from comprehensive, but it can help give you an idea of manufacturers that provide good/poor Linux support, and products that are particularly problematic with Linux/work really well.

As a very general rule, IMHO, nVIDIA tend to provide better Linux graphics drivers than AMD/ATi. 

Good luck!

---

### Post by gadolinio on 2010-06-28
For what I've seen, you can have some trouble getting some drivers, but generally things are pretty easy. Sometimes drivers are already there when you install ubuntu -- and with windows you need to install them.
Even when I thought some things could not be achieved (and decided the sacrifice was worth it, because of the overall system advantages), I ended up finding a solution in these forums, in launchpad, or in some other website.
Bluetooth, specific window themes, NVIDIA drivers to enhance graphical effects, device management, software management. These are some things which I couldn't perfectly use for a while, and then doing a deeper research got the expected solutions. But generally, everything was easy to configure (when needed) and use.
Dual booting with windows is a good choice if you're used to that OS, and even once you get used to linux you might well keep win just in case. If you have the hard disk space, no need to bother erasing it.
Feel free to reply for any specific question you have.
Good luck!

---

### Post by Smart Viking on 2010-06-28
> **rollin said:**
> Just a suggestion but try the Ubuntu Live CD. Test the system when running to see what works with the drivers and stuff and what doesn't? Should be cool!
At least that way you can test your system and not worry about installation yet.
1+

Burn the iso image to a cd and boot from it, if everything works nicely on the live system, it should work just as good after you have installed it. (only faster since it will boot from the HDD and not the CD) :)

---

### Post by JC Cheloven on 2010-06-28
I have an Asus P5W DH moterboard and everythink works fine with linux. Graphics card could be a concern, find out if it's supported and your trouble will be, hopefully, minimal ;-)

---

### Post by rollin on 2010-06-28
> **Smart Viking said:**
> 1+

Burn the iso image to a cd and boot from it, if everything works nicely on the live system, it should work just as good after you have installed it. (only faster since it will boot from the HDD and not the CD) :)

+1 (lol)
Also on your new system if you originally install XP, which is fair enough if that is what you are familiar with, you can also go to the halfway measure by using the WUBI install.

Essentially if you like the live CD and want to start making changes simply boot XP, insert the live CD and choose "Install inside Windows" choose the file size carefully and you'll have a fully running Ubuntu OS to choose from at boot, along with XP, without having to worry about dual booting yet. You can make changes and stuff and if you want to remove it, boot into XP and simply remove "Ubuntu" from Add/Remove Programs and it will be gone completely!

Also forgot to say welcome too! ;-) Lots of clever friendly people and good support. Enjoy!

---

### Post by warfacegod on 2010-06-28
Wubi is a decent *short term* alternative. It was never intended as a permanent install but as a trial.

I agree with everyone's suggestions about doing your homework on your hardware and using a LiveCD or even better a LiveUSB. You can create one with unetbootin.

The only thing that realy sticks out to me is the power supply. 350 watts seems a little skimpy to run that rig. Especially if you'll be using a capture card.

---

### Post by Ziton on 2010-06-28
> **warfacegod said:**
> 
The only thing that really sticks out to me is the power supply. 350 watts seems a little skimpy to run that rig. Especially if you'll be using a capture card.

I have a 480w but it doesn't  have  a sata power connector. Could I get an adapter for it?

---

### Post by CharlesA on 2010-06-28
> **Ziton said:**
> I have a 480w but it doesn't  have  a sata power connector. Could I get an adapter for it?

If it's got Molex connectors, you can find adapters for Molex to SATA. :)

---

### Post by aphatak on 2010-06-28
I have a set-up with a 350 watt power supply, and it works fine.  I have TWO 500GB hard drives.
Like you, I started out with a dual-boot version, but I haven't booted Windows for at least a couple of months.
I have a Hauppauge HD-DVR (an external device, connects to a USB port, and allows you to record 1080p HD via component input), and a Diamond 7.1 channel sound card.  Drivers for both of these were found and installed without any fuss when I installed Ubuntu 10.04 LTS.  I have a 3 GHz Pentium D, but the CPU is not even breathing hard when playing movies with 7.1 channel surround sound.
Choose your hardware well, and I don't think you will run into problems.

---

### Post by gadolinio on 2010-06-29
+1 to what rollin, Smart Viking, and warfacegod say; That's actually the ideal order in which you should start using ubuntu: liveCD---> if you like it---> wubi. Test it deeply, install applications, work, etc. ---> if you like it (now that you have really tested it)---> full install.

---

