---
title: "Random crashes while web browsing"
date: 2010-05-06
forum: General Help
---

### Post by JustinFischer on 2010-05-06
(Update 5/19: I can now reproduce the bug either booted normally or from the live CD)

I've got the strangest bug and no idea what is causing it. While web browsing, sometimes the OS will completely crash. The crash always goes the same way:

First, it shows some text on the screen too fast for me to read, but it looks like red ASCII bullet points followed by white text, both over a black background. 

[FONT="Fixedsys"][COLOR="Red"]*[/COLOR] SOMETHING SOMETHING
[COLOR="Red"]*[/COLOR] SOMETHING SOMETHING
[COLOR="Red"]*[/COLOR] SOMETHING SOMETHING[/FONT]

After doing this for about half a second, it enters some kind of loop. The top half of the screen alternates between black/white vertical bars and solid black, while the bottom half of the screen remains solid black.

The only way I've been able to get out of this is by pressing the power button, and doing so shows me the *buntu logo (currently using Xubuntu) and then turns itself off.

Here's why I can't figure out what's wrong:
[LIST]
[*]The crash happens in GNOME, KDE, and XFCE. I have since uninstalled KDE because I was just checking to see if it still crashed.
[*]Both Firefox and Google Chrome cause the crash.
[*]No other programs seem to crash this way; just the web browsers. I've played games and listened to music for hours with no problems.
[*]Opening the same pages doesn't reproduce the crash. It happens randomly every hour or so.
[*]Even simple pages (like tabs of JPEGs with no HTML) cause the crash.
[*]This is a recent install from an Ubuntu 10.04 CD.
[*]I was previously using Kubuntu 8.04 and had no issues.
[/LIST]

---

### Post by deancasino on 2010-05-08
Same here too! Mem test for 24hours, no worries. Sadly, I can report I don't get this problem with Windows 7...

---

### Post by JustinFischer on 2010-05-10
Progress! I can now reproduce the crash at will. When I go into my GNOME screensaver settings, it shows the walking ant with a spotlight for a second, and then goes straight to the black/white vertical bars part of the crash.

I'm not certain that it's the exact same thing as the web browser crash, but it certainly seems similar.

---

### Post by JustinFischer on 2010-05-19
I can also reproduce it when I boot to the Ubuntu live CD. Any ideas for how I can narrow down the cause of this bug? :confused:

---

### Post by CFury on 2010-05-19
I have a similar issue, however my screen just goes black and then loads the login screen.  Sometimes it's happens when I'm typing in the Google searchbar, and sometimes it happens when a busy page is loading.  Frequent updates have made the issue rear it's ugly head less and less so I'm thinking it's just minor bugs that are currently being worked out.  Additionally I'm using Namoroka as my browser, so this could also be part of the issue.

Cheers,
C

---

### Post by mdtimepc on 2010-05-19
Using Ubuntu 10.04 and I also have had this issue both when on the web or returning to the desktop from a running screensaver. However, after the last round of updates I have not had the issue in the last couple of days. Hope it is fixed now. :)

---

### Post by mr clark25 on 2010-05-19
i have had a very similar problem on a motherboard that i was playing around with. whenever i would put my system under load (especially heavy graphics), i would get that black/white screen.

turns out my voltage regulators were overheating. i put a fan on them, and the problem stopped.

i havent ran update manager for a while, i will see if it helps...

---

### Post by emanuel.b on 2010-05-19
Have you guys tried turning off Compiz? Also, check for updates too.

Just to let you know, I've been having the same problem too. Except it's only when I connect to wireless networks, or leave it connected idle for long periods of time...

---

### Post by KuroChou on 2010-05-20
I can replicate this crash 100% when attempting to load openGL graphics, but it will do so randomly as well.
Holding Ctrl+Alt+Delete will do a soft reboot, and preserve data (open tabs, unsaved documents etc.).

It happens most often when there are multiple programs running, or when someone clicks or makes too many keystrokes while one or more programs is lagging.

It would be logical to assume that this crash happens as a direct result  of overloading the cpu, or any one of the media controllers.

I can only reproduce this on my clean install (xp to lucid) machine.
I fact, I've not had this happen even once on my upgrade machine (karmic to lucid).

Any ideas?

---

### Post by lukeiamyourfather on 2010-05-20
It sounds graphics driver related but nobody is posting useful information. What graphics adapter, what driver, 32-bit or 64-bit, etc. That information will help to determine if there's a trend with a particular driver or graphics adapter (or something else entirely).

---

### Post by jgschaefer on 2010-05-20
I encounter this issue almost every time I browse the web; I have a new Xubuntu 10.04 32 bit install on a Dell M40 laptop, using a Nvidia Quadro2 card and the Ubuntu supplied Nvidia driver.  Never had an issue running Ubuntu 9.10, or previous versions.

---

### Post by JustinFischer on 2010-05-20
I'm using 32-bit Ubuntu/Xubuntu. I've uninstalled Compiz and still get the crash, so it's not that. Here's my sysinfo:


System information report, generated by Sysinfo: 5/20/2010 8:49:06 PM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 10.04 (lucid) release.
	GNOME: 2.30.0 (Ubuntu 2010-03-31)
	Kernel version: 2.6.32-22-generic (#33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010)
	GCC: 4.4.3 (i486-linux-gnu)
	Xorg: unknown (23 April 2010  05:11:50PM) (23 April 2010  05:11:50PM)
	Hostname: explodicle-desktop
	Uptime: 0 days 0 h 7 min

CPU INFORMATION
	GenuineIntel, Intel(R) Pentium(R) 4 CPU 2.40GHz
	Number of CPUs: 1
	CPU clock currently at 2391.310 MHz with 512 KB cache
	Numbering: family(15) model(2) stepping(7)
	Bogomips: 4782.62
	Flags: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr

MEMORY INFORMATION
	Total memory: 495 MB
	Total swap: 1448 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  Maxtor 6E040L0   
	SCSI device -  scsi1
		Vendor:  _NEC     
		Model:  DV-5800A         

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
		Subsystem: Dell Device 0126
	PCI bridge(s)
		Intel Corporation 82801 PCI Bridge (rev 81)
		Intel Corporation 82801 PCI Bridge (rev 81)
	USB controller(s)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
		Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
		Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	ISA bridge
		Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	IDE interface
		Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
		Subsystem: Dell Device 0126

GRAPHIC CARD
	VGA controller
		Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
		Subsystem: Dell Device 0126

SOUND CARD
	Multimedia controller
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
		Subsystem: Dell Device 0126

NETWORK
	Ethernet controller
		Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
		Subsystem: Dell Device 002e

---

### Post by emanuel.b on 2010-05-21
> **lukeiamyourfather said:**
> It sounds graphics driver related but nobody is posting useful information. What graphics adapter, what driver, 32-bit or 64-bit, etc. That information will help to determine if there's a trend with a particular driver or graphics adapter (or something else entirely).
As I said, I'm only having these problems when connected to my wireless network. Screen goes black with vertical white lines (about 1 pixel thick). Basic computer specs here:

Gateway MT6458 Notebook
160 GB Hitachi Hard Disk
875 MB of RAM
ATI Radeon Xpress 1150 Graphics (No longer supported by ATI. No proprietary driver as of Ubuntu 9.04)
Marvell TopDog 802.11b/g/n Wireless (Won't work in Ubuntu)

I'm using an ATIVA Wireless G PCMCIA notebook adapter to connect to my wireless network.

Could someone tell me what is wrong?

---

### Post by RJQ on 2010-05-21
For any one with the intel 8xx video cards (and similar) this is a well known issue and fixes for this are not expected soon, posible work arounds are found on the wiki, this is a xorg driver problem, i am unaware for the ati or nvidia users.

note: this is a linux wide problem, no matter wich distro you use is not going to work, there are ones that are slightly more stable than others but nothing for sure.
in my machine with chakra on it the crashes are rare now but still present, they are using the 2.6.33.xx, and newer xorg, it may be some hope for this machines....

---

### Post by JustinFischer on 2010-05-21
> **RJQ said:**
> posible work arounds are found on the wiki

Would you please post a link? I can't find it.

---

### Post by RJQ on 2010-05-25
Sorry for late response, in case you still interested this is [the page]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

note: none of those works for my 845 card

---

