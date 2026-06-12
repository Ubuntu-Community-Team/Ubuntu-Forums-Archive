---
title: "nvidia-xconfig"
date: 2010-10-02
forum: General Help
---

### Post by otnarg on 2010-10-02
HI GUYS.
I'M FAIRLY NEW TO UBUNTU AND LOVE IT. I'M WANTING TO GET COMPIZ WORKING AGAIN AND GET MY TV TO WORK WITH MY HDMI PORT. I'VE LOOKED ALL OVER GOOGLE FOR ANSWERS BUT CAN'T FIND A SIMPLE STEP BY STEP GUIDE TO HELP ME. TRIED TO GET NVIDIA TO WORK BUT ALL I GET IS 

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I'VE MESSED AROUND FOR HOURS NOW AND GOT NO JOY AS YET,,, MY MISS'S IS NOT IN THE BEST MOOD NOW LOL. SO THOUGHT I'D PUT A POST ON FOR YOU GUYS TO DIG ME OUT. THANKS OTNARG:P

---

### Post by Johnny B on 2010-10-02
have you tried installing the restriced drivers through system > administration restricted drivers? 
once you have them installed run 'gksu nvidia-settings'
also check system > preferances > appearence and go to the visual effects tab.

---

### Post by luvshines on 2010-10-02
Do you have proper Nvidia drivers installed ??

Check System->administration->hardware drivers

Make sure that you have the 'recommended' Nvidia drivers installed and active

---

### Post by wojox on 2010-10-02
Did you run 

```
sudo nvidia-xconfig
```

To create a new xorg.conf file for your system? Then

```
gksudo nvidia-settings
``` 

To configure nvidia to meet your needs?

---

### Post by otnarg on 2010-10-02
in the hardware drivers its blank????

---

### Post by otnarg on 2010-10-02
wojox all i get with your 1st command is 


Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by wojox on 2010-10-02
> **otnarg said:**
> in the hardware drivers its blank????

Is this a fresh install as of recently?

---

### Post by wojox on 2010-10-02
> **otnarg said:**
> wojox all i get with your 1st command is 


Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Good, that's what you want. Now run the other command.

---

### Post by otnarg on 2010-10-02
in the hardware driver box its says at the top no proprietary drivers in use on this system

---

### Post by otnarg on 2010-10-02
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  


did the other command and it came up with this

---

### Post by wojox on 2010-10-02
Yeah you need that driver. Try running an update:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by otnarg on 2010-10-02
Is this a fresh install as of recently? yes and no. i uninstalled them and put them on again but had the same result

---

### Post by otnarg on 2010-10-02
wojox done the update and checked the hardware drivers and still nothing there :-(

---

### Post by wojox on 2010-10-02
> **otnarg said:**
> Is this a fresh install as of recently? yes and no. i uninstalled them and put them on again but had the same result

You lost me here. You uninstalled the drivers?

---

### Post by otnarg on 2010-10-02
yes got rid and put back on. when i start ubuntu now it tells me i'm starting in low graphic mode. so far with ubuntu i've stumbled around ok and got on ok with it... but this time i'm at a loss. thanks for you time with this mate

---

### Post by otnarg on 2010-10-02
any help would be g8

---

