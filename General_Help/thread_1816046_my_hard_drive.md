---
title: "my hard drive"
date: 2011-08-01
forum: General Help
---

### Post by cold37 on 2011-08-01
my desktop pc was messing up bad and i had too take out the hard drive and put it in my other desktop it works great but theres one thing it dont see my video card how can i get it too look for it? it was a nVidia and now Video adapter
	Intel® Graphics Media Accelerator 950

---

### Post by cold37 on 2011-08-01
Processor, Operating System and Memory
Processor
	SR5010NX PC: Intel® Celeron® D Processor 360
&#8226; 3.46GHz, 512KB L2 Cache, 533MHz Front Side Bus
SR5030NX PC: Intel® Pentium® 4 Processor 641 HT Technology
&#8226; 3.2GHz, 2MB L2 Cache, 800MHz Front Side Bus
Operating system installed
	Genuine Windows Vista&#8482; Home Basic
Chipset
	Intel® 945GC Express Chipset
Standard memory
	SR5030NX PC: 1024MB
SR5010NX PC: 512MB
Memory type
	DDR2-SDRAM
Memory slots
	SR5030NX PC: 2 DIMM (240-pin, DDR2) (occupied)
Internal drives
Internal hard disk drive
	SR5010NX PC: 120GB SATA
SR5030NX PC: 160GB
Hard disk drive speed
	(7200 rpm)
Optical drive type
	SR5030NX PC: SuperMulti DVD Burner
SR5010NX PC: SuperMulti DVD Burner with LightScribe Technology
Optical drive speed
	SR5010NX PC: 16x DVD±R, 8x DVD+RW, 6x DVD-RW, DVD-RW, 8x DVD+R DL, 4x DVD-R DL, 5x DVD-RAM, DVD-RAM, 16x DVD-ROM, 40x CDR, 32x CDRW, CDRW, 40x CD-ROM
Second optical drive speed
	SR5030NX PC: 16x DVD±R, 8x DVD+RW, 6x DVD-RW, DVD-RW, 8x DVD+R DL, 4x DVD-R DL, 5x DVD-RAM, DVD-RAM, 16x DVD-ROM, 40x CDR, 32x CDRW, 40x 40x CD-ROM
System features
Modem
	56k modem
Network interface
	Ethernet 10/100BT integrated network interface
Video adapter
	Intel® Graphics Media Accelerator 950
Video RAM
	SR5030NX PC: 32MB dedicated graphics memory. Up to 224MB Total Available Graphics Memory as allocated by Windows Vista&#8482;
SR5010NX PC: 32MB dedicated graphics memory. Up to 64MB Total Available Graphics Memory as allocated by Windows Vista&#8482;.
Internal audio
	High Definition Audio, 6 speaker configurable
Keyboard
	SR5030NX PC: Compaq keyboard
SR5010NX PC: Compaq scroller mouse, Compaq keyboard
External drive bays
	SR5010NX PC: &#8226;2 external 5.25"(one available) &#8226;1 external 3.5" (one available) &#8226;1 internal 3.5" (occupied)
SR5030NX PC: 2 external 5.25"(one available) 1 external 3.5" (one available) 1 internal 3.5" (occupied)
Expansion slots
	SR5010NX PC: &#8226;2 PCI slots (1 available) &#8226;1 PCI-E x16 slot (available) &#8226;1 PCI-E x1 slot (available)
SR5030NX PC: 2 PCI slots (1 available) 1 PCI-E x16 slot (available) 1 PCI-E x1 slot (available)

---

### Post by 3rdalbum on 2011-08-01
Someone else will surely say it, but your thread title doesn't reflect your question; you might get better help if you put something like "Ubuntu doesn't see my video card" as the thread title.

Ubuntu is expecting to be displaying video through an Nvidia graphics card as with the old computer. This device doesn't exist anymore, but the Nvidia driver has put references to it throughout your xorg.conf. What you should probably do is remove the xorg.conf file (/etc/X11/xorg.conf). This forces X to detect your hardware on each startup.

It will then make the decision to use the Intel graphics, rather than being "forced" to output to a non-existent Nvidia card by the xorg.conf.

How do you remove the xorg.conf file when you can't see anything on the screen? Well, when you press Control-Alt-F1 you should get a text terminal on the screen. Regardless of your X settings. You can use this to move the xorg.conf file:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

(note: Don't ever remove configuration files, just rename them so they are not recognised. Just in case you need the original file back. This is what I've done in this command)

One reboot later, you should have a graphical desktop on your Intel graphics.

If this doesn't fix your problem and the thread doesn't get any more useful posts, send me a PM and I'll try to help more.

---

### Post by cold37 on 2011-08-01
it did not work?

---

### Post by pqwoerituytrueiwoq on 2011-08-01
so you had a nvidia gpu now you have a intel card right?
sudo apt-get remove nvidia-cruuent
if you installed the driver with nvidia's run file
sudo nvidia-installer --uninstall

---

### Post by Topsiho on 2011-08-01
Hello cold37,

Sorry for not answering your question, but according to the information you give you still use Xubuntu 8.04. Though this is an LTS version, it is already more than 3 years old, and not supported anymore. LTS on the desktop is supported for 3 years, ordinary versions 18 months.

So the best thing you can do is install a newer (X)Ubuntu. If you prefer LTS than (X)Ubuntu 10.04 is the way to go, which will be supported until April 2013.

Possibly this may solve your problem in one lucky stroke :)

Topsiho

---

### Post by cold37 on 2011-08-01
i have ubuntu one computer with a build in video card and it die i take out my hard drive out of it and put it in a pc i was not using and now i cant get ubuntu to see my new build in video card

---

### Post by 3rdalbum on 2011-08-02
Probably need some more information.

When you boot up the computer, do you see your BIOS's startup screen (where it checks the memory and stuff)?

What part of the procedure didn't work? Did it all seem to go okay but you still didn't get a GUI desktop, or were there any error messages along the way? If you can describe exactly what happened and exactly what happens during startup we might be able to figure out why the adapter isn't working.

Also, is it turned on in the BIOS?

And which version of Ubuntu are you using?

Does a live CD work? (if it doesn't, then there's probably some sort of hardware problem, or the onboard graphics is turned off in the BIOS).

---

### Post by cold37 on 2011-08-02
11.04

---

