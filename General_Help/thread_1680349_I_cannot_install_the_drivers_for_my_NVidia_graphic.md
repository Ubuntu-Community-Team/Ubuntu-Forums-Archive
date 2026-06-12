---
title: "I cannot install the drivers for my NVidia graphics card, I am new to Ubuntu."
date: 2011-02-02
forum: General Help
---

### Post by MisterPowers on 2011-02-02
I was up all night trying to install my card, I have the file from the NVidia site, I have it checked to run as execute but it wants me to run it as root, so I brought it up in Terminal and ran it as sudo but when I get to the password it wont let me enter it. And I've tried just typing it and hitting enter even though I cant see the password but that doesn't work. I cant find any way around it or any way to fix it. Is my computer just not qualified to run Ubuntu 10.10?

Also, I have to do all of this in safe mode because I attempted to install the drivers in the normal screen and it wouldn't start up after it asked me to reboot. 

Upon initial installation everything was askew. The resolution was way off.

Please help.

---

### Post by VCoolio on 2011-02-02
First of all, you don't see the password when you type it, so that's correct. Second, you don't need the file from the nvidia site and install the driver manually. You can use System > Administration > Additional drivers. Also see [this page](https://help.ubuntu.com/community/BinaryDriverHowto).

---

### Post by Dans564 on 2011-02-02
yea like vcoolio said, don't use the one from nvidia's website.  That is way to complicated.  Just go to System--->administration--->additional drivers.  The app does the rest.  Oh make sure u have a working Internet connection

---

### Post by drewsus on 2011-02-02
Get the most up to date drivers via system updates with this PPA:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

Reboot.

Easy as eating pie that someone else made for you.

---

### Post by steveneddy on 2011-02-02
> **drewsus said:**
> Get the most up to date drivers via system updates with this PPA:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

Reboot.

Easy as eating pie that someone else made for you.

Ooo - that looks cool - I just love a well executed ppa.

---

### Post by MisterPowers on 2011-02-02
Actually I used the system updater to update it but it caused Linux to boot improperly and just sit there. So I'm trying to install it directly from the site.

---

### Post by drewsus on 2011-02-02
Did you read my post? Or anyone elses for that matter? They suggest to not download it from the site. 
And I provided 4 easy commands to add a repository the the nvidia drivers and install them.

---

### Post by IWantFroyo on 2011-02-02
Note: I am assuming you are using a laptop. I have (some) experience with laptop booting problems.
Try doing Additional Drivers again, then rebooting and pressing ESC until you come to a screen with some choices. Go to something that looks like Linux Generic 2.6.... and press e. 
Now put pci=noacpi in. The best place to put it is after the two letters a bit past the middle of the paragraph: ro 
If that doesn't let you boot or messes up your touchpad, try acpi=off in the same spot pci=noacpi used to be.

---

### Post by MisterPowers on 2011-02-03
That PPA worked, thanks a bunch man. But now my microphone wont work. :( I cant find it with any of basic stuff. Like the audio settings and whatnot. This is bumming me out.

---

### Post by drewsus on 2011-02-03
I dont have too much experience with this, but what if you run: 
```
pavucontrol
```
And go to the Input Devices tab. Can you see anything worthwhile here?

---

### Post by MisterPowers on 2011-02-04
No. :-\
I've been tryin to fix it and I saw some stuff on updating the kernel and whatnot but I'm not sure how to do any of that and I don't even know if it'd work.

I have a Sony VPCF115FM. Don't know if that helps.

---

### Post by drewsus on 2011-02-04
link to this "stuff" please. 
And maybe a screen shot of what you see from pavucontrol that I directed you to?

---

### Post by drewsus on 2011-02-04
also, does this help at all?
[http://ubuntuforums.org/showthread.php?t=1526178](http://ubuntuforums.org/showthread.php?t=1526178)

---

