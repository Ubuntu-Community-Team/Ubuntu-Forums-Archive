---
title: "Ubuntu 10.04 doesn't boot with the latest kernal?"
date: 2010-04-29
forum: General Help
---

### Post by bgrohe on 2010-04-29
After I upgraded from 9.10, I restarted and waited. ubuntu boot screen froze after a little bit, and the my caplock and scrolllock started flashing (I believe this is the kernel panicking) Then I tried safe mode and it did the same thing when is was saying something about sensors. So I then went to grub and started it with an old kernel and it booted fine (without the splash screen though) what should I do?

EDIT: ok the kernel version it is not working with is version 2.6.32-21 and it does work in 2.6.31-21. Also, it now doesn't say anything about sensors. It panics after App-armor loads ans skips Firefox's profile (or something like that)

---

### Post by bgrohe on 2010-05-01
I think i have figured it out. If I install NVIDIA Driver 173 it works. If I install the Current version, it doesn't. also if I use the opensource driver (I forget the name) it works? is this a bug with the new driver?

---

### Post by coffeecat on 2010-05-01
> **bgrohe said:**
> I think i have figured it out. If I install NVIDIA Driver 173 it works. If I install the Current version, it doesn't. 

There may be an issue with your specific nvidia card. The current nvidia driver (195) works just fine here with the 2.6.32-31 kernel and a GeForce 8400 GS card. Which video card do you have?

---

### Post by bgrohe on 2010-05-01
It is an EVGA e-Geforce 6200 PCI graphics card

---

### Post by GSF1200S on 2010-05-01
> **coffeecat said:**
> There may be an issue with your specific nvidia card. The current nvidia driver (195) works just fine here with the 2.6.32-31 kernel and a GeForce 8400 GS card. Which video card do you have?

As it does here on a 9800GTX+, but not without some trickery. 9.10 booted perfectly fine on this computer (stats sig), but after installing 10.04 with the Alt CD, it froze in the same fashion as the OP is describing. 

I managed to get things functioning by doing the following:

Boot in using your 173 drivers. Open a terminal and run:
```
sudo gedit /etc/default/grub
```
and find the line that says:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
(or whatever it has in the " ")and change it to:
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Save and close gedit.
Then go back to the terminal and run:
```
sudo apt-get update
```
Go to System>Administration>Hardware Drivers and enable the latest nvidia drivers. Go back to the terminal and do:
```
sudo nvidia-xconfig
sudo update-initramfs -u
sudo update-grub
```
Restart the computer and hopefully it will boot for you.

---

### Post by bgrohe on 2010-05-01
Ok, I will try that later, but is there a chance that it will break my system, I don't have time to fix any more problems currently (busiest time of the year for me).

---

### Post by GSF1200S on 2010-05-01
> **bgrohe said:**
> Ok, I will try that later, but is there a chance that it will break my system, I don't have time to fix any more problems currently (busiest time of the year for me).

Yes, there is a chance. Perhaps you might want to stick with the 173 drivers until you get some time? It wouldnt really create any new problems, just bring back to life the issue you are having when you enable the 195 drivers. You should have no issues reverting to 173 if you have an issue.

---

