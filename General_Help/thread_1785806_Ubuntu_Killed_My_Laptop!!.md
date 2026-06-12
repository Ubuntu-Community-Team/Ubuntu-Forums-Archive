---
title: "Ubuntu Killed My Laptop!!"
date: 2011-06-18
forum: General Help
---

### Post by GMarkow on 2011-06-18
Hi all,
Here's my story....
I have a Dell Inspiron 700m. I've been running Ubuntu since 2008. Every time I re-install the O.S. I have to alter the video driver. When 10.04 was released it crashed the system and I couldn't figure out how to fix it so I left Karmic on and all was well. Well the DVD/CD drive never worked right under Karmic but no big deal.

Anyway, last week I attempted an upgrade. Everything went fine until upgrade finished and it was time to reboot. 

Reboot hung, so I ended up killing the power and  doing a cold boot.
Now when booting from the hard drive, I get a brief flash of the Ubuntu welcome screen (in the wrong resolution) and then things die. I'm left looking at a grey curser in the upper left.

Worse yet, I can't boot from a live CD or USB. Neither, Ubuntu, openSUSE or Puppy Linux will boot from CD or from USB. 

I double checked my boot order in the BIOS and still nothing boots. I reset the BIOS to factory Default, still nothing boots. I disabled the hard-drive in the boot up order in the bios and still nothing boots. 

I can't figure out what happened and I can't access the machine at all exepet to enter the BIOS. 

Can anyone give me a hand with this???
Thanks in advance,
Greg

---

### Post by goldshirt9 on 2011-06-18
can you run a live cd of ubuntu

---

### Post by GMarkow on 2011-06-18
No, nothing boots. I tried live CD's and USB boot up's of Ubuntu, Puppy Linux and OpenSUSE. None boot.

---

### Post by aeronutt on 2011-06-18
Does it have a discrete graphics card?

---

### Post by dFlyer on 2011-06-18
Please don't blame Ubuntu for killing your laptop. Many things can be your cause. Have your checked your hd with disk utilities? What's your video card? Have you checked your memory to see if the ram has gone bad? What have you tried to fix things with? Seem if other distros cd can't boot maybe your cd/dvd has gone bad. I doubt it's Ubuntu fault.

---

### Post by GMarkow on 2011-06-18
Your right it may not be Ubuntu. However, this occurred immediately after an upgrade.

---

### Post by GMarkow on 2011-06-18
No not to my knowledge. The graphics card is intergrated and has always been an issue. But ususally just a matter of fixing the screen resolution. I acutally higly suspect the graphics card/driver but since I can't access the system at all at this point I'm stuck.

---

### Post by pqwoerituytrueiwoq on 2011-06-18
Can you get to the bios settings?
edit i guess so can you run a ram test?
you may be able to bypass the video driver issue using the alternate install disk and then install the right driver from recovery mode after installing
edit never ever had issues with intel gpus on Ubuntu
  you can try adding this ppa and installing updates
**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**

---

### Post by GMarkow on 2011-06-18
Yes I can access the BIOS.
BIOS shows no options to test the ram.
What is the "alternate install disk"? Can I access recovery mode without it?

---

### Post by lidex on 2011-06-18
> Now when booting from the hard drive, I get a brief flash of the Ubuntu welcome screen (in the wrong resolution) and then things die.
Do you mean the grub screen? Or gdm? Or plymouth?
Hold down the shift key while booting from hdd to see if you can pull up grub screen.

---

### Post by pqwoerituytrueiwoq on 2011-06-18
> **lidex said:**
> Do you mean the grub screen? Or gdm? Or plymouth?
Hold down the shift key while booting from hdd to see if you can pull up grub screen.
my money is on plymouth and the behavior says there is a nvidia-current driver installed
if that is the case it would explain a lot since the system has a intel gpu

alt cd
[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

