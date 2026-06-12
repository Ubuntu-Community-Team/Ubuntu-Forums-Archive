---
title: "switching to Ubuntu from windows"
date: 2010-11-26
forum: General Help
---

### Post by denwy8 on 2010-11-26
Hello, I am a windows user and I am pissed with it. I want to switch to ubuntu but I just want to know if I would be able to use Autodesk Maya 2011, 3ds max 2010, autocad 2010 and CorelDraw X5 without any problem if I started using Ubuntu.

I know there are alternatives for these softwares that would run smoothly in ubuntu but I am very much comfortable with these that I don't want to use any other applications and these are the ones i'm using at school as well. So if anyone could assure me that I can still use these applications without problems then I'll make the switch A.S.A.P thanks. :p

btw, this is the specs of my laptop that I'm using


Display
Diagonal Size : 14" 
Max Resolution : HD (1366x768)

Processor (CPU)
Type : Intel® Core&#8482;2 Duo Processor

Chipset
Type : NVIDIA® MCP79MVL

Memory
DDR2 667/800
2GB

Graphics Card
NVIDIA® GeForce 8200M G
share with system memory

Hard Drive
250GB SATA 2.5"


Communication
Modem : No modem port
LAN : 10/100
WLAN : 802.11b/g/n
Bluetooth : optional

Input
87 keys keyboard

Audio System
2 High Quality Stereo Speakers

Interface
1 x D-Sub (VGA)
3 x USB 2.0 port
1 x Mic-in/Headphone-out

Optical Drive
Super-Multi

Slots
Card Reader : SD/MMC/MS/MS Pro

Camera
1.3MP

Power
Battery : 6/9 cells
AC Adapter : 65W

Operating System
Genuine Windows Vista® Home Premium

Dimensions and Weight
Width : 344.4 mm
Depth : 212 mm
Height : 13.5-28 mm
Weight : 2 kg

---

### Post by nothingspecial on 2010-11-26
> **denwy8 said:**
> 

I know there are alternatives for these softwares that would run smoothly in ubuntu but I am very much comfortable with these that I don't want to use any other applications 

Hi and welcome.

You may have some luck with wine.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

But if you continue thinking that way you are going to have a frustrating time using linux.

If there is windows software you simply cannot do without, dual boot

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by wilee-nilee on 2010-11-26
Make sure Ubuntu runs with live cd then dual boot until you really want to get of windows. Personally I would at the least have the ability to reinstall windows if you have a license and key.

---

### Post by wet-willy on 2010-11-26
Although I have no insight on wine, I doubt most of those apps. are ported through wine.
But....
I don't see any problems...here's what to do:
Install virtual software, VMware or open source, install Windows as a guest, use for 30 days and pay up, run your apps. in an environment you are familiar with, when not working, shut down Windows guest and Virtual client and keep on Ubuntuing' with full memory.

---

### Post by hawthornso23 on 2010-11-26
I differ from the others here. I recommend going cold turkey. Find free equivalents and learn how to use them. This method is a little tougher at the start, but much easier in the long run. Trying to maintain a dual boot system or windows on a virtual machine or using WINE all the time is a PITA.

---

### Post by jim_deadlock on 2010-11-26
#5 +1

If you are (rightly) peeved with windoze, why try to hang on to parts of it? It may seem like a slightly frightening step to completely dump what you're used to, but I predict you'll be glad you did within a week.

Edit: one tip, make sure you're on a wired connection during your first system updates, that way ubuntu will install your wireless drivers for you, then you can painlessly go back to wireless when you're done.

---

### Post by wilee-nilee on 2010-11-26
Geez I'm a full open source user started with it and I keep my XP and W7 installed at the least to help others. Advising somebody to go cold turkey is kookie.:confused: :rolleyes: :shock:

---

### Post by jim_deadlock on 2010-11-26
With dual boot you have to reboot every time you want to switch, which is a pain. What's wrong with running your windows in virtualbox when you need to?

---

### Post by jroa on 2010-11-26
Thumbs up for virtualbox.  You can run Windows in Linux for the occasional Need-Windows-for-this-application.  If you mostly use Linux for you daily needs, then why dual boot for the occasional stuff when you can run Windows in Linux?

---

### Post by wilee-nilee on 2010-11-26
> **jim_deadlock said:**
> With dual boot you have to reboot every time you want to switch, which is a pain. What's wrong with running your windows in virtualbox when you need to?

Did you say cold turkey see post 5. Besides it takes about at the most 2 min to reboot into W7 from maverick for me. I have XP on a virtual though. Linux has a learning curve, especially if your used to MS.

What is a pain to you is a pain to you right.;) No pain here on my end just noticing the programs that the OP needs means they will need windows probably anyway.

---

### Post by wet-willy on 2010-11-26
Regarding my first post, I promote a virtual environment solely to promote Ubuntu. Personally, I only do the virtual thing on a machine with no less than 4GB of memory, on my laptop with only 2GB memory, the virtual angle is rarely used as it's too much of a lag. 
I multi-boot my units, my fave. desktop with 4GB memory still suffers when running a VM. I'm a speed freak, and to date, I have not had a system good enough to go without multi booting, because nothing beats full memory and full processor resources available to "ONE" operating system.
I'll reboot any day before going solo with VMs for the sake of performance, at least for now till I get with the times.

---

### Post by denwy8 on 2010-11-26
okay... I am quite confused...

---

### Post by denwy8 on 2010-11-26
What's the difference bet. WINE and Virtualbox? Sorry to sound like a noob.. :(

---

### Post by WildOscar on 2010-11-26
> **denwy8 said:**
> What's the difference bet. WINE and Virtualbox? Sorry to sound like a noob.. :(

--WINE--
is a Software Library to run Windows Based software in Linux. WineHQ has a list a windows software that work with WINE and also guide to get them working.

--VIRTUALBOX-- 
Similar to VMWARE where u run a Virtual-PC and Install any OS and run. VirtualBox also has a seamless mode for Windows XP.

Using VIRTUALBOX (and good hardware setup) you can pretty much everything ur normal windows will run but this is slow and resources are shared between the Primary OS (Linux) and the Virtual OS

WINE allows you to run the Windows Application only without having to run the complete OS.

Hope this helps :)

---

### Post by Goldfissh on 2010-11-26
I'd go with the Virtualbox method, it's probably the best if you want to switch over to Linux but don't want to completely ditch windows.

---

### Post by bullium on 2010-11-26
Quick run down on virtualaztion.
Terms you should know and understand:

Host = Main computer (Your Dell laptop)
Guest = Virtual Machine or VM running under the host machine
Your setup would look like this:
Host (Ubuntu) -> Guest VM (Windows)

Your can read more at the [virtualbox.org]("http://www.virtualbox.org/wiki/End-user_documentation") site. 

With that being said here is what I run on a daily basis at work. I run Ubuntu 10.04 LTS x64 on a Intel Q6600 (Quad core) CPU with 8GB of RAM and a 256MB Nvidia video with it's own DDR memory. 

I run VMWare Workstation 7.x (like virtualbox only commercial applications) and run Windows 7 x64 as a guest OS on that system. I only give the VM 1.5GB of ram and 1 processor and it runs remarkable stable and smooth, as well as the host. 

With your current setup of only 2GB of memory that your video shares, you will most likely need to upgrade your memory to say 4GB which will be needed for good performance with your memory intensive applications listed. Since your system is a dual core system you can give one CPU to your virtualized Windows machine and the other CPU will be used for you host (Ubuntu install) machine.

I think you'll be happier utilizing the virtual option rather than messing with Wine or dual booting.

---

