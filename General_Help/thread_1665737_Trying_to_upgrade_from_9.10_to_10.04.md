---
title: "Trying to upgrade from 9.10 to 10.04"
date: 2011-01-12
forum: General Help
---

### Post by modmidget on 2011-01-12
I'm trying to upgrade from Ubuntu 9.10 to 10.04, but not having much luck.  I've followed the Ubuntu instructions to download the upgrade ISO file and burn it to a CD.  I inserted the upgrade cd in the the drive after booting into Ubuntu and I got the message popup saying the upgrade had been detected. I clicked on OK or Upgrade and Synaptic Package Manager opened.  At that point the Ubuntu installation instructions say to follow the on-screen instructions, but I did not get any on-screen instructions.  I clicked on Mark All Upgrades and it installed 7 small files, but that is it.  

I don't know what to do next.......  The Ubuntu installation instructions are NO HELP at all and when I put the ISO CD  in the drive I no longer get the message saying an upgrade had been detected.

Can someone please provide me with **_detailed_** instructions on how to do this upgrade?  I really don't know very much about Linux and I'm lost.

Thank you.

Ken

---

### Post by cariboo on 2011-01-13
You probably would be better off doing an in place installation. Boot from the Live CD and and once at the screen wher you choose to install or try ubuntu, click the install button. When you get to the patitionin section choose manual partioning. Once at the partition screen select the partition where Ubuntu is installed, and click the change button, select to use the partition as ext3, ext4 or whatever file system you originally setup, select the mount point, but make sure you don't select the format option. Once you have finished select he partitions click the next button and follow the instructions.

---

### Post by veggen on 2011-01-13
Is the regular upgrade through the Update Manager out of the question (no internet connection etc)?

---

### Post by modmidget on 2011-01-13
Thank you for you reply cariboo907, I'll take a look and see if that will work.  But that brings up another question.  If I install the upgrade will my programs and files be erased?  I have a couple of Windows programs installed via Wine.  Will I lose those?  I also maintain one of our checking accounts using GNUCash.  Will I lose my data files?

Next concern....  The Ubuntu PC is connected to my network via a PCI wireless card.  The card is a Zyxel Zyair 300g.  I purchased this card because it was 100% compatible with Ubuntu 8.04 and did not require ndiswrapper.  It has continued to work with v8.10, v9.04, and v9.10, but now I'm wondering if it will continue to work with 10.04.

Veggen, I don't want to try the live update via the internet because the PC is connected via the wireless connection and it would take many hours to do the download and install.  I went this route when I upgraded from 8.04 to 8.10 then again going from 8.10 to 9.04 and once again going from 9.04 to 9.10.  As I recall, a couple of those upgrades ran all night.

---

### Post by modmidget on 2011-01-13
I may have answered my own question about the Zyxel wireless PCI card.  I booted the PC from the Live DC, went into terminal mode, and enter  "lspci -v | less".  The resulting list shows a wireless network card that is a clone of a Z-Com, Inc XG-900.  

Now I've got to try to figure out why I'm not getting a connection.

---

### Post by modmidget on 2011-01-13
Well, maybe didn't answer my own question about the wireless card.  I typed in *iwconfig* and I got this list:

lo        no wireless extensions.

eth0      no wireless extensions.


There is nothing listed for wlan0, so I guess it doesn't see the the card after all.

*****   EDIT  *******

I just typed in the command  *sudo ifconfig wlan0 up* and got a message that said:   ERROR while getting interface flags:  No such device

---

