---
title: "Shut Down, Printer &amp; Broadband Problems"
date: 2009-11-21
forum: General Help
---

### Post by gestanu1 on 2009-11-21
As a trial I have recently installed Ubuntu 9.04 from disk as a clean install wiping all old files etc on an old computer with 256MB RAM & 20GB HD and Epson printer and broadband modem connected.  Install went OK Ubuntu and desktop etc looks good.

Problem 1: system does not detect my printer and modem.
Problem 2. computer hangs when shutting down with error message "System Halted"

I have reinstalled same Unbuntu with same results.  Please, can anyone advise how to resolve these problems.

I have since received a Ubuntu ver. 9.10 disk.  Will it install over present ver. 9.04 and might it solve the above problems?

I have just downloaded Ubuintu Pocket Guide but have not yet studied it - maybe some specific pages will solve my problems??

Eary response appreciated.  Thanks  :eek:

---

### Post by blazemore on 2009-11-21
Hello, welcome to the Ubuntu Forums. I hope you'll find everyone friendly and helpful.

I would certainly recommend installing the later version of Ubuntu.
The more recent version has improved hardware support, and might fix your issues for you.

What model of printer do you have, specifically? You say it's an Epson, but Epson makes a lot of different printers! It should say on the printer itsself somewhere.

When you say broadband modem, how is it connected to the computer? Is it connected via USB? Ethernet? Or maybe wireless? Without knowing this, and also the specific make (and model) of the modem, it is more difficult to solve your problem.

With regards to your shutdown problem, I would be surprised if installing 9.10 doesn't solve it right away. There really is no compelling reason for non-uber-geeks to use 9.04 instead of 9.10.

I hope this helps. Please report back to let us know if upgrading has solved your problems (or not!)

EDIT: I would also recommend doing a **clean install** (ie not an in-place upgrade), wiping your disk and installing from your new disk from scratch. If you have any important data you **must** back it up, because wiping your disk will obviously lose everything that's currently on it!

---

### Post by gestanu1 on 2009-11-23
Many thanks for your quick response.  I will do a clean install of ver 9.10 - there is no data yet on this old computer.  I will reply again when I have installed this.  Meanwhile ......

My Printer is the Epson model RX500 - maybe I can download and Epson driver for the Ubuntu - will check.

The broadband modem is a Sagem F@st 400 make with only the one computer connection, nothing else connected apart from the telephone line.  But I may later reconnect it to my wireless modem router Thomson model TG585v7 which I use for my main desktop computer and is working fine.

By the way is there any means (tick of box etc) for me to be advised when a reply is made to my posts, as for other forums.

---

### Post by gestanu1 on 2009-11-25
I have now made a clean (whole c: drive) install of Ubuntu 9.10 with my above printer USB and power connected, and modem USB cable and power connected and note the following:
   
  Ubuntu finds the printer and I have printed a line from the word processor program, but not the modem which only shows the power light and not the ADSL light.
   
  On shutdown the system hangs showing following message:
  “ Ubuntu 9.10 Trident-desktop tty”: on top line and 
  “Trident-desktop login:  [ 251.0419341 System Halted” on second line
  (same error message as when ver 9.04 was installed previously).
  The screen goes dead but computer fan etc is still operating – pressing the power switch on front of computer then shuts it down fully.  (Note Trident is the name I called the computer.)
   
  Question 1. – How to get Ubuntu to fully shut down the computer via the Ubuntu screen??
   
  Question 2. How to get Ubuntu to recognise my modem and allow me to input my ISP [www.tiscali.co.uk]("http://www.tiscali.co.uk/") and password, incoming mail server pop.tiscali.co.uk , outgoing mail server  smtp.tiscali.co.uk and  password??
   
  Question 3. How access the computer BIOS – previously with WinXP via ‘Del’ during stratup??
   
  Question 4. With previous WinXP system pressing F8 key during startup allowed alternative startup modes (eg. Safe Mode with minimum drivers installed) – is there something similar with Ubuntu??

Hoping for an early response/resolution. Thanks.  :icon_frown:

---

### Post by JKyleOKC on 2009-11-25
> **gestanu1 said:**
> By the way is there any means (tick of box etc) for me to be advised when a reply is made to my posts, as for other forums.
When you start a thread or post a reply, the forum software automatically subscribes you to that thread. At the top of the first page when you come into the forum you'll find an item "Quick Links" and if you click it you will get a drop-down menu. Near the bottom of that menu you'll see "Subscribed threads." Click that and you get a list of the threads to which you are subscribed. Each will have a check box to its right, and will show you the notification choice presently in force. To get immediate Email notification of replies, check the box, then go down to the pull-down box next to the Go button, pull it down, and choose the action you want. Then click Go and it will be set up for you.

You can also use this capability to cancel subscriptions to threads that are no longer of interest to you. I subscribe to threads that have information I may want to reference in the future, in addition to the automatic subscriptions such as the one I'll have to this thread...

---

### Post by gestanu1 on 2009-12-04
Repeat message as there was only a part answer before.

I have now made a clean (whole c: drive) install of Ubuntu 9.10 with my above printer USB and power connected, and modem USB cable and power connected and note the following:
   
 Ubuntu finds the printer and I have printed a line from the word processor program, but not the modem which only shows the power light and not the ADSL light.
   
  On shutdown the system hangs showing following message:
  “ Ubuntu 9.10 Trident-desktop tty”: on top line and 
  “Trident-desktop login:  [ 251.0419341 System Halted” on second line
  (same error message as when ver 9.04 was installed previously).
The screen goes dead but computer fan etc is still operating – pressing the power switch on front of computer then shuts it down fully. (Note Trident is the name I called the computer.)
   
  Question 1. – How to get Ubuntu to fully shut down the computer via the Ubuntu screen??
   
  Question 2. How to get Ubuntu to recognise my modem and allow me to input my ISP [www.tiscali.co.uk]("http://www.tiscali.co.uk/") and password, incoming mail server pop.tiscali.co.uk , outgoing mail server  smtp.tiscali.co.uk and  password??
   
  Question 3. How access the computer BIOS – previously with WinXP via ‘Del’ during stratup??
   
Question 4. With previous WinXP system pressing F8 key during startup allowed alternative startup modes (eg. Safe Mode with minimum drivers installed) – is there something similar with Ubuntu??

Hoping for an early response/resolution. Thanks.  :icon_frown:

---

### Post by plucky on 2009-12-04
> Question 1. – How to get Ubuntu to fully shut down the computer via the Ubuntu screen??

What are the specifications of your computer.I had a Pentium 3 with 256MB which wouldn't shutdown completely and I added "acpi=force" to the kernel line when the system boots and that fixed that problem.

For 9.10 ```
gksudo gedit /etc/default/grub
```
search for the line that says ```
GRUB_CMDLINE_LINUX=""
``` and add "acpi=force" so it looks like ```
GRUB_CMDLINE_LINUX="acpi=force"
```

Then from a terminal run ```
sudo update-grub
``` to update the grub configuration file.See if the system shuts down now.
> 
Question 2. How to get Ubuntu to recognise my modem and allow me to input my ISP [www.tiscali.co.uk](www.tiscali.co.uk) and password, incoming mail server pop.tiscali.co.uk , outgoing mail server smtp.tiscali.co.uk and password??


You cannot have a modem/router and a DSL modem attached to the same telephone line.It won't work.

Connect the Ubuntu machine directly to the modem/router using an ethernet cable,or get a wireless USB dongle that works with Ubuntu and connect that way.It will save a lot of problems in the future.


> Question 3. How access the computer BIOS – previously with WinXP via ‘Del’ during startup??

The BIOS has nothing to do with Ubuntu.You should still be able to access the BIOS as you did before using the <DEL> key during the POST (power on self test) when the computer is powered on.

> Question 4. With previous WinXP system pressing F8 key during startup allowed alternative startup modes (eg. Safe Mode with minimum drivers installed) – is there something similar with Ubuntu??

Use the <ESC> to open the "grub" menu.By default in Karmic,the grub menu is not displayed during the boot process.
In that menu,there is an option to boot into "recovery mode".


Good Luck

---

### Post by gestanu1 on 2009-12-05
Thanks Plucky for your quick response, but I comment as follows using the same item nos:

1. My computer is a Pentium 3 with 256kRAM and 20GB HD.  I am confused of how to get to the pages to use the gksudo and GRUB commands - please expalain??

2. Obviously some misunderstanding - I was not trying to use two modems simultaneously.  I was sung my old ADSL (Sagen F@st 400) modem which Ubuntu did not recognise.  Later I may instead try my new wireless modem router (Thomson model TG585v7) [directly connected ie. not using the Etherrnet ports] presently connected to my desktop WindowsXP machine, but am not sure if the driver for this will be suitable for Ubuntu/Linux and may have to see if another driver is avaialble??

3. Thanks, I have now used the Del key to get the BIOS up.

4. Please explain how to get the GRUB menu??

Early response appreciated.  Thanks.

---

### Post by plucky on 2009-12-05
> I am confused of how to get to the pages to use the gksudo and GRUB commands - please expalain??

Open **Applications > Accessories > Terminal** and input the "gksudo gedit" command,will open the file /etc/default/grub in an editing window with super user privileges, so be careful.


> Later I may instead try my new wireless modem router (Thomson model TG585v7) [directly connected ie. not using the Etherrnet ports] presently connected to my desktop WindowsXP machine, but am not sure if the driver for this will be suitable for Ubuntu/Linux and may have to see if another driver is avaialble??

Very unlikely you will need to install a driver to get your ethernet port working,just select the network icon on the top panel and enable DHCP for the wired connection.The modem/router should have more than one ethernet port,mine has 4,so you should be able to connect both the ubuntu machine and the XP machine,so they can both access the outside world.

> 4. Please explain how to get the GRUB menu??


Just after the POST has finished,just tap the <ESC> key on your keyboard and the Grub boot menu should open.
<ESC> = key at top left of keyboard

Good Luck

---

### Post by gestanu1 on 2009-12-13
Thanks again Plucky for your response.  I have tried your suggestions with the following results:
   
  1. I opened Ubuntu Applications>accessories>terminal>input GKsudo edit> a new small window comes wanting Password which I enter.  This quickly brings me back to the previous page then after a few seconds a new window comes headed ‘Unsaved “myname@computername-desktop”.  What do I do here??
   
  Nowhere can I see “file /etc/default/grub” and did you really mean “etc” or was the “etc” just typical for something else??
   
  Hence I cannot enter ‘gksudo gedit /etc/default/grub’ as you previously suggested to find ‘GRUB_CMDLINE_LINUX=""’ to add line ‘GRUB_CMDLINE_LINUX="acpi=force"’ and later ‘sudo update-grub’.
   
  2. Regret that I don’t have an Ethernet connection on my Ubuntu computer to link directly with my wireless modem router and will need an Ethernet card in the future.
   
  So for the time being I would like to get my ADSL Sagem F@st 400 modem recognised and working some how??  Do I need a Linux driver for this Modem??  If so will contact Sagem UK to try to download the driver via my other computer– and then how to install it on the Ubuntu computer, via a USB stick??

---

### Post by plucky on 2009-12-13
> Nowhere can I see “file /etc/default/grub” and did you really mean “etc” or was the “etc” just typical for something else??

You have to enter the whole command as you are editing the grub file which is located in /etc/default directory.So open a terminal and enter this command ```
gksudo gedit /etc/default/grub
```
Linux is case sensitive,so enter the command as shown or copy and paste it into the terminal window.

The file looks like ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="05"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

Change it,save it and then run "sudo update-grub" in the same terminal window.

> So for the time being I would like to get my ADSL Sagem F@st 400 modem recognised and working some how?? Do I need a Linux driver for this Modem?? If so will contact Sagem UK to try to download the driver via my other computer– and then how to install it on the Ubuntu computer, via a USB stick??



Don't know this modem,recommend getting an ethernet card or a compatible USB wireless stick.Sorry

Good Luck

---

### Post by gestanu1 on 2009-12-15
Thanks again Plucky for your reply 13 Dec.
   
  1) I entered the code as suggested and after realising that there was a space before the /etc/default/grub I was able to get the file as you list.
   
  I then added "acpi=force" so the line Code: was GRUB_CMDLINE_LINUX="acpi=force" as advised by your response 3 Dec.
   
  I then clicked Save at the top, and then ran "sudo update-grub" in the same terminal window.  The shut down and the previous “System halted” error did not arise and the screen blanked – good, but the computer was still running and was shut down by its button.  On restart I was able to show that my new Code still existed.  So your suggestion has been partly successful but did not fully shut down the computer????  Any other ideas??
   
  2) I phoned Sagem (France) about my modem (Sorry correct model is Sagem F@st 800 – not 400!!!) and was advised that this is now an old model and will not handle Linux.  They suggested to search the Ubuntu forum for a Linux driver for this modem, or to purchase an Ethernet card for my computer so that I can link directly to my other wireless-modem-router, or a wireless dongle to link to the latter wirelessly.  I am thinking about this but would hope that item 1) above can first be solved.
   
  However, I see there is quite a lot about this Sagem modem on the Forum but it is all rather confusing and not referring to my Ubuntu Ver. 9.10.  What is Debian?? Also various comments about headers and kernel??  From the Forum can you spare the time to point me to a specific clear simple solution to try??  Presumably I would have to download some info and/or driver - and then how to input that into the computer via USB maybe??

---

### Post by plucky on 2009-12-15
> So your suggestion has been partly successful but did not fully shut down the computer???? Any other ideas??


Try some other kernel boot options. See section **kernel options** in the "Common Boot Options" heading in this [link]( https://help.ubuntu.com/community/BootOptions)

> However, I see there is quite a lot about this Sagem modem on the Forum but it is all rather confusing and not referring to my Ubuntu Ver. 9.10. What is Debian?? Also various comments about headers and kernel?? From the Forum can you spare the time to point me to a specific clear simple solution to try?? Presumably I would have to download some info and/or driver - and then how to input that into the computer via USB maybe??

From what I have seen on the Forums,there was a driver for your modem which used to work with previous versions,but the download website is no longer active and there is no further development of the driver for USBDSL modems.I would seriously get a wireless USB dongle or a wireless PCI card and connect to your wireless router.

Checkout this [link](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) for supported wireless adapters.

Debian is another linux distribution. See [link](http://www.debian.org/)


Good Luck

---

