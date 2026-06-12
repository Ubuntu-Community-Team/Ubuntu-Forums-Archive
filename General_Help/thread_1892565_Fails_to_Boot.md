---
title: "Fails to Boot"
date: 2011-12-08
forum: General Help
---

### Post by Janeleaper on 2011-12-08
I have a Dell 530 running Ubuntu 10.04.

For the last few days my computer has failed to recover from suspension.  I got a message saying it failed to detect my graphics settings and gave me the option of low graphic mode.  I also kept getting the red triangle indicator that I needed to run update manager, but when I did so, I got the message not all packages were downloaded.

Then this morning, it failed to boot. I've not been able to get it to boot from the 10.04 CD either.

I get the following on screen:

A lot of numbers then:

Killed 
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on/ root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootary

BusyBox v1.13.3(Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 1.780023] usb commands4-2: new low speed USB device using uhci_hcd and address 3
[ 1.979275] usb 4-2: configuration #1 chosen from 1 choice
[2.252072] usb 5-1: new low speed USB device using uhci_hcd and address 2
[ 2.4274821 ] usb 5-1: configuration #1 chosen from 1 choice

That's it.  I tried typing help but the screen does not respond to the keyboard.  I have no idea what to do.

---

### Post by BC59 on 2011-12-08
You have to search if you have a hardware problem. Check your HDD for errors.

---

### Post by Janeleaper on 2011-12-08
How do I do that?

---

### Post by BC59 on 2011-12-08
Boot with a Live CD and from the Disk Utility, check to the left pane for your HDD and the to the right find the SMARTdata. From there do a check to see if you have a problem.

---

### Post by Janeleaper on 2011-12-08
It won't boot from cd.  The boot priority is removable device 1st, and I've put the cd in the drive, but I still get the screen I've described.

---

### Post by BC59 on 2011-12-08
Well try this, if you can do something:

[http://www.bootmed.com/](http://www.bootmed.com/)

---

### Post by Janeleaper on 2011-12-08
OK I'll try that.

---

### Post by Janeleaper on 2011-12-08
It turns out the pc that has broken down was the only one in the house with a cd/dvd rw drive, so I can't burn a disc and as far as I can see -- I'm screwed.  

I doubt whether it would have worked anyway.  The 10.04 cd I'm trying to boot from was fine when I installed the OS on a netbook a couple of weeks ago.

---

### Post by BC59 on 2011-12-08
The Bootmed can be installed on a USB pendrive.

---

### Post by Janeleaper on 2011-12-08
It tells me that I have to download and install virtualclonedrive to make a usb.  Tried that.  It is an exe file for Windows, so I can´t install.  I searched synaptic package manager for a similar piece of software, but could not find anything.

---

### Post by BC59 on 2011-12-08
You can do that perfectly with Startup Disk Creator of Ubuntu.

---

### Post by Janeleaper on 2011-12-08
Sorry, I don´t understand.  Start up disc creator makes start up discs from cds, but I don´t have a cd/rw drive to make the cd.  

I feel like I&#7743; going round in circles

---

### Post by BC59 on 2011-12-08
It's the same tool to create CDs or USBs. Choose the .iso file and then the output. It has an option if you like to erase the USB.

---

### Post by Janeleaper on 2011-12-08
I´ve had a look at the bootmed file I downloaded.  It is also an exe file.  The bootmed site does say specifically that it is designed for Windows users.  Since I don´t use Windows, I can´t see how it is of use to me.  I can´t install it, and since I can´t get the Ubuntu cd to boot, there is no reason to think the bootmed would either.

But thanks for your help. Anything was worth trying.

---

### Post by BC59 on 2011-12-08
In that case try to make an Ubuntu installation USB, to see if you can boot with it.

---

### Post by Janeleaper on 2011-12-08
OK  

The functioning desktop has a wifi connection.  So I'm not hopeful that I could download the iso from Ubuntu successfully.  However, I could possibly make the usb from the 10.04 cd.  I have an external cd drive (which isn't rw).  I've plugged in the usb and the external cd drive to the computer and inserted the 10.4 cd, but can't work out what to do next.

---

### Post by BC59 on 2011-12-08
You can create a .iso file from the CD.

Inset the CD on the computer and run

```
sudo dd if=/dev/cdrom of=ubuntu.iso
```

It will be created a file with the name ubuntu.iso on home directory.

---

### Post by Janeleaper on 2011-12-08
I get:

dd: opening `/dev/cdrom': No medium found

---

### Post by BC59 on 2011-12-08
Looks like your CD player is not working. Sorry!

---

### Post by Janeleaper on 2011-12-08
I tried it with the Lubuntu 11.10 cd as well and got the same response.  

Places computer shows a cd/dvd drive

---

