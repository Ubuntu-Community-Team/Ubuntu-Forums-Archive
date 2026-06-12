---
title: "Screen Freeze after startup"
date: 2011-11-28
forum: General Help
---

### Post by flyingcircle on 2011-11-28
Hey all,

I have an HP dv6 laptop and I have recently installed Ubuntu 11.10. I was previously having problems with a black screen, but that problem was solved by adding "nomodeset" after "quiet splash" in the boot command line.

My current problem is that soon after start-up into ubuntu the system freezes and my Caps-Lock LED starts blinking. Anyone have a gander as to what I can do to solve this?

Thanks

---

### Post by ventrical on 2011-11-28
> **flyingcircle said:**
> Hey all,

I have an HP dv6 laptop and I have recently installed Ubuntu 11.10. I was previously having problems with a black screen, but that problem was solved by adding "nomodeset" after "quiet splash" in the boot command line.

My current problem is that soon after start-up into ubuntu the system freezes and my Caps-Lock LED starts blinking. Anyone have a gander as to what I can do to solve this?

Thanks


Can you get terminal?

<Ctrl+Alt+F1>

---

### Post by flyingcircle on 2011-11-28
No I'm not able to access the terminal. it is a complete freeze

---

### Post by ventrical on 2011-11-28
> **flyingcircle said:**
> No I'm not able to access the terminal. it is a complete freeze


Is that 64bit AMD series?


I'm not sure right off hand what it could be.

I'll check into it.

Edit:

 I have had problems with keyboards and I just opt out to change keyboards and that works in a lot of cases - but not if you do not have any extra keyboards laying around :) I recall I had the same problem a while back and I am totally drawing blanks at the moment :(

---

### Post by ventrical on 2011-11-28
You can still get a terminal by inserting your install disk and booting up. When the install screen asks you if you want to install or try ubuntu just press <Ctrl+Alt+F1>

This will give you a terminal.

Type in :
lspci <Enter>

and report back the video card adapter.

---

### Post by flyingcircle on 2011-11-28
well i am able to do a few things. ubuntu freezes about a minute or two after i start up.

here is the lscpi output:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9641
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

---

### Post by ventrical on 2011-11-28
Ok.. thanks for the info. I think what we have to do here is edit your GRUB file on the harddisk where you have your install on 11.10 Ocelot.

  To do this you would have to use your Oneiric Install disk (since you cannot get a terminal). You would want to choose "Try Ubuntu" option **THEN** open your home directory, click on Filesystem (this will mount your hdd) navigate to /usr/share/grub/ default/ and then  open the grub default file:

You should get something like this:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

**and you will want to change the value in the command line:**
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

  I am assuming that there is a problem between the ATi driver, he ATi adapter card and the monitor.

 You will have to do this in #root so the command would be:
sudo -i

 when it asks for a password you would just hit enter  and it should go to root terminal where you can edit that file.

  If you accomplish this and then reboot and actually get to the grub screen you can run the Recovery Option and then choose a normal boot from there.

  of course others may chime in on this with their advice also.

 I am going to try this right now on my own 64bit system.


 Let me know how it works out.

---

### Post by flyingcircle on 2011-11-28
Like I said in the first post, I had the black screen problem and I added nomodeset to in addition to quiet splash. Is this going to make a difference if I delete quiet splash?

---

### Post by ventrical on 2011-11-28
> **flyingcircle said:**
> Like I said in the first post, I had the black screen problem and I added nomodeset to in addition to quiet splash. Is this going to make a difference if I delete quiet splash?


 Actually I just tried this method and it failed. Something I missed in the code. So I will have to ask you to belay my last message . I'll try to search about on this.

---

### Post by ventrical on 2011-11-28
All I know at this point is that you can use the Live CD to get to browser and terminal to repair your broken system. Sounds to me like it is a GRUB problem but then it could be many different things.

  I am just assuming from the informations so far that you should be able to do a clean install of Oneiric on your PC but something went south , it appears, during the installation process.

 When I do fresh installs I choose updates and thirdparty software  from the installer and DO NOT encrypt. I have had great success so far with a few borks here and there. I wish I could be of more help.

---

