---
title: "Beginners guide to installing graphics drivers?"
date: 2012-08-25
forum: General Help
---

### Post by robhill19653 on 2012-08-25
Hello, due to lack of support, i've given up on pclinux and I will be switching to Ubuntu. I've downloaded the ISO and will be burning the cd to install shortly. 

My problem is I just don't understand how to get my graphics card drivers installed, (as well as my printer or wifi). I've been searching the forums here for solutions but haven't found one yet. I'm just out of my element with Linux in general and unfamiliar with using the command line or even knowing "which" command window to use. I can't even seem to find "which" drivers to use for my graphics card. There are multiple options with little explanation on which driver I would need. (frustrating).....
Can someone direct me to a simple step by step process for finding the correct drivers and installing them? I know I'm not the first person "new to linux" to have these issues and I'm hoping that since Ubuntu is the most supported distribution, I would be able to find the help I need. I was hoping there would be a nice "sticky" in the forums specifically addressing these "known issues with linux". Help?

I have:

an Nvidia GeForce GT520 graphics card (PCI express)
A Lexmark 2500 series All In One Printer, (usb) and
A Netgear wireless n 150 usb adapter wna 1000

Additional info if needed:

-Asus motherboard (I don't remember the model)
-AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (2000 Mhz)
-4 Gigs of DDR2 800 Mhz RAM in dual channel mode
-500 Gig SATA Drive (dual boot with Windows XP)
-1 Terabyte SATA Drive (storage for Windows)
-one each, cdrw and dvdrw with light scribe.
-current updated bios. The bios are all set to default except I've turned off the parallel and serial ports and told the motherboard I'm using an add in video card.
:confused:

Thank You.

---

### Post by SeijiSensei on 2012-08-25
Find the "Additional Drivers" application and run it.  It should handle all the rest.

---

### Post by irv on 2012-08-25
Here is what I would suggest. Burn the DVD and boot into the live OS off of it. (Do not install yet). After it loads and is running see what is working. Check to see if your wifi is up and running. If it is then run Additional Drivers utility you should see the driver for your video. If you do, then do the install of the OS, and when doing the OS install you can pick the option to run along side Windows.

Once you are up and running you can install the driver for your video.
Remember you have to jump into the water to learn to swim.

---

### Post by robhill19653 on 2012-08-27
So I was more worried than I needed to be. As Ubuntu 12.04 was installing, it found my WIFI and configured it. After it was installed, I found an icon next to the "mail" icon that was flashing. Presto, it was letting me know there was a new driver for my video card! I still can't seem to get the printer working though. I found a post that suggested installing the driver for the Lexmark 2600, when it fails it will leave 3 config files I can edit to make it work. Unfortunately, I haven't been able to find "that" driver.
Ubuntu has come a long way since I first tried it back in 2003. I've got the "compiz fusion" working now that my graphics card has an updated driver. Very nice looking OS now.

---

### Post by jim_deadlock on 2012-08-28
Glad to see you had success. The general advice regarding drivers on fresh installs is to make sure you have an ethernet cable plugged in during the install, that way Ubuntu can find your drivers easily and you can unplug it and use the wifi when you're done. Might be useful for future reference.

Regarding your printer, is it USB or wireless or what? Normally you would just start up the 'Printing' app, click the Add button and go from there.

---

### Post by robhill19653 on 2012-08-29
> **jim_deadlock said:**
> Glad to see you had success. The general advice regarding drivers on fresh installs is to make sure you have an ethernet cable plugged in during the install, that way Ubuntu can find your drivers easily and you can unplug it and use the wifi when you're done. Might be useful for future reference.

Regarding your printer, is it USB or wireless or what? Normally you would just start up the 'Printing' app, click the Add button and go from there.

It is a usb printer.
I tried the "printing app" but it failed to install.
I found a post somewhere that said  you could do a work around by trying to install the Lexmark 2600 driver and when it fails, go to the 3 configuration files created during the attempt and edit them to make my Lexmark 2550 work. The problem is I can't find those drivers either.
I'm running a dual boot with Windows XP so, for now, I can just boot into Windows if I need to print but I'd like to get this working properly in Linux. So far I'm very happy and impressed with the current Ubuntu. The last time I tried it was back in 2003 or 2004.

---

### Post by irv on 2012-08-30
I just tried to add a driver without having the printer that you have, and I selected add printer and typed in this url.
```
Ipp://cups-server/printers/printer-queue
```
Select your make printer and looked through all the drivers. I didn't see your model, but maybe you could use one that would work. It would be worth a try. If it doesn't work you can always remover it.
You could also do a search for a "Generic text-only" driver that would work for printing text to not have to switch to Windows to just print a text file.

---

