---
title: "Nvidia driver problems"
date: 2009-12-06
forum: General Help
---

### Post by thebrandon on 2009-12-06
I have tried every way possible to install the nvidia driver always with the same tragic results.  I am using Ubuntu 9.10 64 bit and I am trying to install the driver for my nVidia Corporation NV18 [GeForce4 MX 4000] videocard but when I tried strait from nvidia, through envy, or with the Hardware Drivers option in the System>Admin menu the screen goes blank just before it loads the login screen and I have to start in recovery mode and remove the driver.  My only real goal for getting this driver installed is to utilize the tv out function which I had working until earlier this year when it screwed up.  I was running the 32 bit version on ubuntu at the time and figured a fresh install of the 64 bit version would help.  It did not.

---

### Post by Malta paul on 2009-12-06
Try this link:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)
Hope it helps you ;)

---

### Post by thebrandon on 2009-12-06
Yeah I tried that too and still the same results.  Crazy right?  I have tried to uninstall and reinstall the drivers every way I can think of and it always ends with a blank screen!

---

### Post by Malta paul on 2009-12-06
Well the way I've installed Nvida drivers is:
a)First download the latest driver for my graphic card and put it on my desktop (its a .tar file)
b)Use > sudo /etc/init.d/gdm stop < to remove the original file.
c)Reboot the computer into the 'Recovery mode', go to the terminal. 
d)CD to / then home/"NAME"/Desktop (with a Capital D) Type 'ls' to read driver.
e) sudo sh ./---Driver--- (case sensitive again)
f) Press Enter and follow the NIVIDA install instructions.
g) Reboot again

Good luck :D

---

### Post by Zoot7 on 2009-12-06
What driver are you using? 
Chances are it might not be compatible with the kernel, i'm using the 190.42 driver and it's working okay.

Generally it's not too difficult to install them.
Download the driver file from [**nVidia.com**]("http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk")
```
sudo service gdm stop
```
This will kill gdm, and X and take you to a prompt.
```
cd <path to driver .run file>
sudo sh NVIDIA*.sh
```
Accept all the prompts including to create a new xorg.conf file.
Then either reboot or run
```
sudo service gdm start
```

---

### Post by Uncle Spellbinder on 2009-12-06
nVidia 190 driver: 

```
#### Nvidia Vdpau Team PPA
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
``` 

[[IMG]http://content.imagesocket.com/thumbs/video_nvidia18d5.png[/IMG]](http://imagesocket.com/view/video_nvidia18d5.png)

---

### Post by thebrandon on 2009-12-06
The driver I installed was :

NVIDIA-Linux-x86_64-96.43.14-pkg2.run

I also tried 96.43.13 as recommended by envy.

I am going to try right now to add the Nvidia PPA and install through the hardware drivers function.

190 isnt showing up.

---

### Post by thebrandon on 2009-12-06
Yeah I reloaded synaptic and rechecked in update.  No go on the 190 showing up.

The kernel I am using is : 2.6.31-16-generic

---

### Post by Zoot7 on 2009-12-06
> **thebrandon said:**
> Yeah I reloaded synaptic and rechecked in update.  No go on the 190 showing up.

The kernel I am using is : 2.6.31-16-generic
You could try downloading the installer and running it directly like I posted above.
[http://www.nvidia.co.uk/object/linux_display_amd64_190.42_uk.html](http://www.nvidia.co.uk/object/linux_display_amd64_190.42_uk.html)

---

### Post by thebrandon on 2009-12-07
Ive tried that too with the same results but I have yet to try it with an older version of the driver, I dont know if that would help but Im willing to try anything!

---

### Post by Zoot7 on 2009-12-08
Normally the best thing to do is to install the version that the Hardware Drivers tool recommends.

---

