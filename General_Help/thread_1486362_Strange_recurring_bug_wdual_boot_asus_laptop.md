---
title: "Strange recurring bug w/dual boot asus laptop"
date: 2010-05-17
forum: General Help
---

### Post by ironstove on 2010-05-17
Hi, I have an ASUS A2K laptop that is running 9.20 and windows 7. 

Usually when I boot up my computer, I go to the grub menu and see a list of choices I can boot into and there is a timer on the bottom o the menu counting down and I can  boot into any of the options fine, but today I booted up my computer and I noticed that the timer was gone and when I chose to boot into ubuntu, I was taken to a blank screen then nothing happened after that. 

I have had this problem in the past, and the only thing that comes to mind is that this laptop was made in France, would hardware be an issue in this case? I have many friends that have ubuntu installed on their laptops, some even having used the same CD as me, but none of them have ever run into this issue. 

Every single time I have had to reformat, but I am growing tired of having to do this constantly. Please help.

---

### Post by oldfred on 2010-05-17
Did you recently install any upgrades? Run this to see if something looks out of place.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by ironstove on 2010-05-17
Ok, I finally figured out the problem.

So I tried to boot into recovery mode and I got a warning error about ACPI. I showed it to my friend and he thought that it would be a good idea to turn off ACPI, so he went into the grub menu editor and used the command:

acpi=off 

after the 'no splash' 

So it was changed to 'no splash acpi=off' 

and rebooted and it worked like a charm.

It was only temporary, so when I booted up he did this:

  496  sudo nano /boot/grub/grub.cfg 
  497  sudo update-grub
  498  sudo nano /boot/grub/grub.cfg 
  499  fg
  500  sudo reboot -n

He went into the grub file and then added in the acpi=off again and then used the reboot -n to just restart. Not really necessary.

Anyway, I have come to realize that the laptop is pretty old and apparently it is an issue with the battery that occurs on older comps.

---

