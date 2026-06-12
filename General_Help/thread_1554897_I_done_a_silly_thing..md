---
title: "I done a silly thing."
date: 2010-08-17
forum: General Help
---

### Post by Jahe25 on 2010-08-17
Long story short, I installed wicd and uninstalled NetworkManager before checking whether or not i could connect with wicd, and as it turns out, I can't. >.<

I downloaded NetworkManager on my other computer thinking I could transfer it to this one on a USB stick but none of my sticks are wanting to mount now for some reason.

Is it possible to somehow install NetworkManager using an Ubuntu Live CD?

Anyone have any ideas how I could either get wicd working, or get NetworkManager back?

The specifics of the wicd problem are that it's hanging on Validating Authentication before telling me "Connection Failed: Bad password" 

Cheers in advance.

---

### Post by SlugSlug on 2010-08-17
couple of things you could do:

setup /etc/networking/interfaces file

or try mount that usb stick which may be easer..

open a terminal - plug stick in and type 
dmesg

at the bottom of this you should see somthing like /dev/sdb  detected (not sure of wording its the /dev bit you need.

now type 
sudo mount /dev/sdb1 /mnt
(add that 1 to sdb)

now browse to mnt on the root - hopefully your file will be there..

---

### Post by SlugSlug on 2010-08-17
you could also use apt-cdrom  if you have the ubuntu cd...

[https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

---

### Post by Peter09 on 2010-08-17
You should be able to connect hard-wired without network manager. Then go to the repositories and download the package.

---

### Post by KeyserSoze93 on 2010-08-17
Plug your network cable in and try something like:

```

sudo ifconfig eth0 192.168.1.88

```

Adjust the IP range as necessary...

This should give you access to the network, and allow you to reinstall your packages.

---

### Post by Jahe25 on 2010-08-17
I couldn't get a wired connection either. I eventually got my usb drive working and reinstalled network-manager and network-manager-gnome, and I got the system tray applet back, but it keeps connecting and dissconnecting every 10 seconds or so.

I know it's not the linux way, but i have so few personal files that clean installing and recovering my files from my back-up would've taken about half the time i've been fretting over this. I need my laptop back asap so I think i'm gonna have to do it unfortunately.

Cheers for your help :)

---

