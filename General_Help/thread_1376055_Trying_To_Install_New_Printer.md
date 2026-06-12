---
title: "Trying To Install New Printer"
date: 2010-01-08
forum: General Help
---

### Post by uzzo2 on 2010-01-08
I am trying to install a new printer and delete my old one. It keeps asking for my password, I enter the same one that I log on with. It keeps telling me that the password may be incorrect. To my knowledge, I only know the one that I log on with. Does anyone know what the heck this thing is talking about?

---

### Post by oldfred on 2010-01-08
It should be the same password. Did you hit the caps lock or num lock keys by mistake?

---

### Post by uzzo2 on 2010-01-09
> **oldfred said:**
> It should be the same password. Did you hit the caps lock or num lock keys by mistake?
That's what I would have thought, but I tried umpteen times making sure the cap lock key wasn't on. It says to enter password for localhost, I don't know of any other password I've put on this thing.

---

### Post by uzzo2 on 2010-01-09
Bump: Has anybody got a clue as to how to get around this? I am currently without a printer, I would really appreciate it.

---

### Post by carlosgs91 on 2010-01-09
.

---

### Post by jusitndm on 2010-01-09
> **uzzo2 said:**
> Bump: Has anybody got a clue as to how to get around this? I am currently without a printer, I would really appreciate it.
not sure but maybe a driver from openprinting.org ( [http://www.openprinting.org/driver_list.cgi](http://www.openprinting.org/driver_list.cgi) ) will help (they have .deb format too)

---

### Post by uzzo2 on 2010-01-09
> **jusitndm said:**
> not sure but maybe a driver from openprinting.org ( [http://www.openprinting.org/driver_list.cgi](http://www.openprinting.org/driver_list.cgi) ) will help (they have .deb format too)
Thanks guys, I was actually able to get access by using the command "gksudo system-config-printer". I got the old printer deleted and the new one installed but it won't print. I don't know if it's the driver or what, it's a brother mfc-295cn. It automatically downloaded a driver for a 260c so I don't know if that's the problem or not.

---

### Post by uzzo2 on 2010-01-09
When I open a web browser and enter the following- [http://localhost:631/printers](http://localhost:631/printers), this is what it comes up with.

Description: Brother MFC-295CN
Location:
Printer Driver: Brother MFC-260C CUPS v1.1
Printer State: idle, accepting jobs, published.
Device URI: usb://Brother/MFC-295CN

---

### Post by uzzo2 on 2010-01-10
I wanted to bump this up one more time, hoping someone might be able to help me.

---

### Post by labinnsw on 2010-01-11
[My recommendation to fix the printer problem is here]("http://ubuntuforums.org/showthread.php?p=8645972#post8645972")

[SIZE="4"]_To recover a lost or forgotten Administrative password._[/SIZE]

Reboot the computer
When you see **GRUB**, press Esc.
Select recovery mode.
At the prompt type:
> password <username>
Follow the prompts to reset your password
reboot with:
> reboot

---

### Post by uzzo2 on 2010-01-11
> **labinnsw said:**
> [My recommendation to fix the printer problem is here]("http://ubuntuforums.org/showthread.php?p=8645972#post8645972")

[SIZE="4"]_To recover a lost or forgotten Administrative password._[/SIZE]

Reboot the computer
When you see **GRUB**, press Esc.
Select recovery mode.
At the prompt type:

Follow the prompts to reset your password
reboot with:
Well, I tried that and got to part 2, it didn't create the directory on my desktop. But, it shows up on my printer configuration for some reason. Still won't print anything though, as far as the password thing goes. I can access the configuration by typing "gksudo system-config-printer" into the command line. I then enter my password I use to log in with and it'll let me do anything I want then. But if I go directly to System>Printing, it'll ask for my password for "localhost". I enter the same password and it won't let me have access.

---

### Post by cjazz on 2010-01-11
You might want to try visiting [this page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-295CN") at Brother support and following their instructions for installing a driver specifically for your printer model.

---

### Post by uzzo2 on 2010-01-11
> **cjazz said:**
> You might want to try visiting [this page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-295CN") at Brother support and following their instructions for installing a driver specifically for your printer model.
Already been there, done that to no avail. I am starting to wonder if something is wrong with the printer itself.

---

### Post by uzzo2 on 2010-01-11
Well folks, I let it set for awhile, came back and deleted it, then reinstalled it. It seems to be working fine now, I didn't do anything different than I did the first time. But it's working now, go figure, thanks for all the suggestions.

---

### Post by uzzo2 on 2010-01-11
Maybe I spoke a little to soon, the printer is working, the scanner isn't. I downloaded the drivers for it but I am getting the error "Failed to open device "brother3:bus2;dev1; Invalid Argument." Guess I'll work on that tomorrow.

---

### Post by uzzo2 on 2010-01-11
> **uzzo2 said:**
> Maybe I spoke a little to soon, the printer is working, the scanner isn't. I downloaded the drivers for it but I am getting the error "Failed to open device "brother3:bus2;dev1; Invalid Argument." Guess I'll work on that tomorrow.
I kept after it and finally found the problem, I am going to post it here so maybe it will help someone else.

Ubuntu 8.04/8.04.1, 8.10
    1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
    2. Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

    3. Restart the OS.

---

### Post by Gigaplex on 2010-01-12
> 
I kept after it and finally found the problem, I am going to post it here so maybe it will help someone else.

Ubuntu 8.04/8.04.1, 8.10
1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
2. Edit "0664" to "0666" in "USB devices" section.


That sounds like the wrong solution. Instead of globally allowing access like that, you should add the users that you want to be able to access the device to the correct group.

---

### Post by uzzo2 on 2010-01-12
> **Gigaplex said:**
> That sounds like the wrong solution. Instead of globally allowing access like that, you should add the users that you want to be able to access the device to the correct group.
Well, I don't know how to do that and there's only me and my family that use this machine. So I am not worried about unauthorized use.

---

### Post by labinnsw on 2010-01-13
I am sure there must be some very good reasons why it is considered risky to allow global access to printing, scanning or faxing. I cannot, however, for the life of me, think of a single one. Can anyone point me to an article on the web, in a magazine, or text book that deals with the subject?

---

