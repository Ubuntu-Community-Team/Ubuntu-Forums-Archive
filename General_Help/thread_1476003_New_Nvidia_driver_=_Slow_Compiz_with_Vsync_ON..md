---
title: "New Nvidia driver = Slow Compiz with Vsync ON."
date: 2010-05-07
forum: General Help
---

### Post by Quake on 2010-05-07
I've just upgraded from Ubuntu 9.04 to 10.04 and I have to say it's a mistake. The Nvidia drivers packaged with the distro offers a abysmal performance when "Sync with Vblank", (By abysmal, meaning the cube, the scale animations are slow)

Compiz settings:
Detect Refresh Rate: Not selected
Refresh Rate: 120
Sync to Vblank: Selected.

And unfortunately, it seems they removed the Benchmark module. Will it be a good idea to install the driver from Nvidia's website?

---

### Post by Ginsu543 on 2010-05-07
When you say "nVidia drivers packaged with the distro," do you mean the restricted drivers you can install using System --> Administration --> Hardware Drivers, or something else from the repos? I did a clean install of 10.04 and installed the restricted drivers (nVidia-current=195.36.15) using Hardware Drivers. I tried to recreate your problem but couldn't do it. For me, it makes no difference in Compiz effects if I click on "Sync with Vblank" in Compiz Settings Manager. I don't know if that is because I already have that setting checked on in the nVidia X Server Settings. Have you tried using the nVidia X Serving Settings applet instead of Compiz Settings Manager?

---

### Post by Quake on 2010-05-07
> **Ginsu543 said:**
> When you say "nVidia drivers packaged with the distro," do you mean the restricted drivers you can install using System --> Administration --> Hardware Drivers, or something else from the repos? I did a clean install of 10.04 and installed the restricted drivers (nVidia-current=195.36.15) using Hardware Drivers. 
Yes, those drivers.
So the cube is fast regardless  you if select "Sync with Vblank" or not?

I've /home in another partition so my settings are intact, perhaps I should remove the compiz settings because something has changed from Ubuntu 9.04 to 10.04...

---

### Post by Wizzu on 2010-08-23
I got bitten by this same issue. I wonder if there's a solution?

My Compiz Config refresh rate is 50, and Sync to Vblank was not checked. I turned it on, but no effect. Things are still slow.

It used to be really fast and slick under Karmic. :(

---

### Post by ellgor on 2010-08-24
Hi, 

I was having poor performance, found this guide and it works:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by eeeH on 2010-09-26
Does anyone already tried ellgor sugestion? I'm thinking of give it a try 'cause my compiz performance is actually pretty bad...

---

### Post by rdvon on 2010-11-05
> **ellgor said:**
> Hi, 

I was having poor performance, found this guide and it works:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

I could hug you right now, the speed increase I got from doing this... I don't think I could have fathomed such a thing. C'mon, ubuntu. get this in the repos!

---

