---
title: "Out Of Options On Driver: Solution Or Microsoft"
date: 2010-10-25
forum: General Help
---

### Post by Grey Seal on 2010-10-25
Dell Optiplex, Kubuntu 10.04, FF3.6.11, Clear wi-fi, neatgear router, belkin f5d7050b

Because I cannot download the USB driver I have moved the hardware to the top floor and connected point to point for the ISP. Neither Belkin nor Clear is able to help me. Either there is way to download this driver or I am forced to return to Microsoft.

I understand that that a file must be created, information must be imported for XP to place in it, that it must be wrapped some how that it can be recognized and executed in Linux OS but I programmed in DOS, this is all unknown to me. I do not know how to create the files, how to import the information, how to put it in the file, where to put the file let alone what .exe is here. I don't know where the libraries are here. 

I have searched for other adapters yet I run into the same problem with each. The dry runs went bad and Universe is not available for a year so I am stuck. I must return to my office, I'm in my daughter's bedroom and she will be back next month for the holiday.

Any assistance to retain the OS would be appreciated.

---

### Post by Mark Phelps on 2010-10-25
First of all, you don't run .exe files in Ubuntu.  Those are MS Windows executable files and they will do you no good here.

Second, if you go to the Networking forum and do a search on NDISWrapper, you will find posts outlining how (in some cases) to use the MS Windows networking drivers (and their .inf file) in Linux.

But, those are the ONLY MS Windows drivers you can use. In all other cases, you will need Linux drivers.

Since each hardware situation is different, you would do better (1) searching this forum and/or the other forums, using the make and model of the hardware you want to install.  You might find posts dealing with that specific hardware.  Posting a thread like this, with a list of items, is unlikely to get you much support as each item is different.

---

### Post by SeijiSensei on 2010-10-25
Let's start simply.  Boot Kubuntu, then from the main menu go to Applications > System > Terminal.  Now you'll get a window where you can type commands.  After the dollar-sign prompt, type "lsusb" and hit enter.  Repeat with the command "lspci".  These list all the devices connected to the USB and PCI interfaces.  One of these entries will report the chipset manufacturer of your wireless card.  What is it?

If you can't find it yourself, just post the entire output of these commands inside [noparse]```

```[/noparse] tags.

---

### Post by uRock on 2010-10-25
I have a Netgear USB wireless NIC and the XP drivers didn't work, but what did work was installing linux-firmware-nonfree via Ubuntu Software Center, Synaptic Package Manager, or CLI. Installing that package in 10.04 and 10.10 made the wireless NIC work fine.

If you have to install the XP driver within NDISwrapper, then install the NDISWrapper via the Ubuntu Software Center, so that you get the GUI, then all you have to do is find your driver via [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F5D7050b](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F5D7050b) __where they appear to have a list with the three driver packages you need to download. Then open NDIS Wrapper in the menus at System> Administration> Windows Drivers.

---

### Post by Grey Seal on 2010-10-25
*Let's start simply.  Boot Kubuntu, then from the main menu go to  Applications > System > Terminal.  Now you'll get a window where  you can type commands.  After the dollar-sign prompt, type "lsusb" and  hit enter.  Repeat with the command "lspci".  These list all the devices  connected to the USB and PCI interfaces.  One of these entries will  report the chipset manufacturer of your wireless card.  What is it?*

Thanks,

Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Although my adapter is a 'B'

---

### Post by SeijiSensei on 2010-10-26
A little browsing around suggests that device uses the Ralink RT2500 chipset.  I have a Linksys adapter with the same chipset and had a number of problems with it using Lucid 10.04.  Moving to Maverick has helped a lot.

Might I suggest you try downloading and burning a [Maverick LiveCD]("http://releases.ubuntu.com/maverick/") and booting from that? See if the wireless works then.  If so, you can use the CD to upgrade to Maverick.

You shouldn't need to install any third-party drivers, either.  Ubuntu should detect the card and use the "rt2500usb" driver.

---

### Post by irv on 2010-10-26
I don't know if you have tried this or if it would help. But I had problems with my wifi card in my laptop and all I had to do was: 
System> Administration> Additional Drivers, and it found the right driver and all I needed to do was select it from the list, and I got connected. I had to connect to the Internet via a wire while I did this, then when I disconnect the wire, it found the wireless. I am not using kubuntu, but ubuntu so I don't know if there is a difference.

---

