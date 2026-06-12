---
title: "Several LiveCD/Live USB boot questions."
date: 2009-12-14
forum: General Help
---

### Post by Roasted on 2009-12-14
Question 1 - Using UNetBootin, I put Kubuntu 9.10 32 bit on a flash drive and booted to it. Out of curiosity, I unplugged the flash drive to see what would happen. Kubuntu was still functional on the system. Why? Does it load onto RAM or something?

Question 2 - If I wanted to actually INSTALL a fully functional copy of Kubuntu, not just a LiveCD ISO, but an actual usable copy, what program would I use to make this happen?

Question 3 - I installed "USB Startup Disk Creator" on Kubuntu 9.04 64 bit, which is on my main desktop, and it did not work. I have it in the menu, but when I open it, nothing happens. No errors or anything. Any idea why this is?

---

### Post by tom.swartz07 on 2009-12-14
> **Roasted said:**
> Question 1 - Using UNetBootin, I put Kubuntu 9.10 32 bit on a flash drive and booted to it. Out of curiosity, I unplugged the flash drive to see what would happen. Kubuntu was still functional on the system. Why? Does it load onto RAM or something?

Question 2 - If I wanted to actually INSTALL a fully functional copy of Kubuntu, not just a LiveCD ISO, but an actual usable copy, what program would I use to make this happen?

Question 3 - I installed "USB Startup Disk Creator" on Kubuntu 9.04 64 bit, which is on my main desktop, and it did not work. I have it in the menu, but when I open it, nothing happens. No errors or anything. Any idea why this is?

Hi Roased,

question 1: yep- you got it. the os is loaded live into the ram and run from there. Although, I wouldnt suggest pulling the plug on it very often :P

question 2: Im assuming you mean install on your system? in that case, when you boot from the livecd and see the desktop, there should be an icon to install the os on the computer. its a rather simple walkthrough. you cant 'install' the os on a flash drive, but you could trick the live cd into thinking that it is. head over to pendrivelinux and google casper files for more about that.

Question 3: Perhaps some investigation is in order; try running it from the terminal, ```
sudo usb-creator-gtk
``` and see what it says. Post it here if you cant decipher it yourself.

Hope this helps!

---

### Post by Roasted on 2009-12-14
jason@Area51:~$ sudo usb-creator-gtk
sudo: usb-creator-gtk: command not found


Yet...


jason@Area51:~$ sudo apt-get install usb-creator
Reading package lists... Done
Building dependency tree
Reading state information... Done
usb-creator is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
jason@Area51:~$


Uhh??

---

### Post by tom.swartz07 on 2009-12-14
okay- from your output you have some files to be updated,
so lets run
```
sudo apt-get update && sudo apt-get update
```
That will refresh your updates and apply them; maybe youre missing a file for your usb-creator in there also..

Now try it from the applications menu, or try with ALT + F2 ```
usb-creator
``` It should autocomplete to what the name is. I see you have Kubuntu as your header, so you might have a different version. Either way- this might fix it.

---

### Post by Roasted on 2009-12-14
No idea man. It appears in my panel as if it's loading for a second, then disappears. Gahh!!

However - it seems as if UNetBootin worked fine since I have a bootable LiveUSB flash drive now. But, wtf? Why is Kubuntu/USB Creator being awnry?

---

### Post by C.S.Cameron on 2009-12-15
Not sure about the current situation but I have only been able to get usb-creator to work with Ubuntu, not xubuntu or Kubuntu etc.
To do a full install to flash drive disable your HDD, plug in your Live CD or Live USB, boot and run install.
It will install to the USBb the same as to HDD and have all the same functionality. It will be a bit slower than a HDD install.
You can even run manual partitioning during install if you want a separate home partition.

---

### Post by tom.swartz07 on 2009-12-16
> **Roasted said:**
> No idea man. It appears in my panel as if it's loading for a second, then disappears. Gahh!!

However - it seems as if UNetBootin worked fine since I have a bootable LiveUSB flash drive now. But, wtf? Why is Kubuntu/USB Creator being awnry?

wait.
are you still using 9.04? there were some critical bugs in that version that were fixed for the 9.10 version.

that might be where your problems are coming from.

---

### Post by Roasted on 2009-12-18
Yeah - I'm running Jaunty on my main desktop because Karmic doesn't like playing nice with multiple hard drives.

Here's to hoping 10.04 fixes Karmic's downfalls - but let's not dig up that discussion. :P I do however run Karmic on my work laptop, and it runs beautifully.

---

### Post by tom.swartz07 on 2009-12-19
> **Roasted said:**
> Yeah - I'm running Jaunty on my main desktop because Karmic doesn't like playing nice with multiple hard drives.

Here's to hoping 10.04 fixes Karmic's downfalls - but let's not dig up that discussion. :P I do however run Karmic on my work laptop, and it runs beautifully.

Whelp, theres your problem!

Like you said, UNetbootin works fine, so use that until you upgrade to 10.04

{thread solved}

---

