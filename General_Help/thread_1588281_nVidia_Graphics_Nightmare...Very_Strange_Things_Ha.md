---
title: "nVidia Graphics Nightmare...Very Strange Things Happening"
date: 2010-10-04
forum: General Help
---

### Post by steevven1 on 2010-10-04
So here's the story: I bought an nVidia GeForce 8400 graphics card, because my on-board Intel  one is actually listed all over the internet as being incompatible with  Ubuntu with no fix (it crashed multiple times a day). I installed it  and used Ubuntu's "System > Hardware Drivers" feature to install a  driver for it. Everything worked PERFECTLY, except that it seemed to  play flash videos a bit slowly.

To just mess around and see if I could solve this, I tried installing a beta driver from nVidia for my card.  I downloaded it as a ".run" file, and I had to shut down X and login as root  to install it. The installation went through, and now my computer boots  and says something like, "Ubuntu is running in low-graphics mode...What  would you like to do?" None of the options really seem to help me, but  when I click, "Run in low-graphics mode for one session," the computer  boots normally and brings me to a version of GNOME that looks somewhat  like Windows safe mode (low resolution, etc.). I can do anything here  that I normally could, EXCEPT, and here is the weird part, nothing that  installs software works. Aptitude, "Hardware Drivers," and "System  Update Manager" are all broken now.

So, what I'd like to do is revert to my old graphics driver (the one  found via Ubuntu's "Hardware Drivers" utility) and get Aptitude, etc.  working again. I have no idea what's going on, but upon Googling, here's  what I've tried so far:

1. Installed another, non-beta driver from nVidia (a ".run" file), and rebooted. Nothing happened.
2. Ran "sudo nvidia-xconfig" and rebooted. Nothing happened.
3. Replaced /etc/X11/xorg.conf with a backup file, which was created  before I installed the beta driver, and rebooted. Nothing happened.
4. Ran "sudo dpkg-reconfigure xserver-xorg" and rebooted. Nothing happened.
5. Ran "sudo update-initramfs -u" and rebooted. Nothing happened.

Any ideas at all? My last resort is to format and reinstall Ubuntu, but I  have an Apache server, an ssh server, and a Windows virtual box set up  on this computer, as well as 7 user accounts! It would be a nightmare to  start over.

Thanks,
Steven

---

### Post by steevven1 on 2010-10-04
SOLVED!

For anyone interested, here's what I did:

sudo aptitude update

Suddenly, Aptitude, Hardware Drivers, and System Update started working again. I used "Hardware Drivers" to uninstall and reinstall the nVidia driver, and everything went back to normal!

---

