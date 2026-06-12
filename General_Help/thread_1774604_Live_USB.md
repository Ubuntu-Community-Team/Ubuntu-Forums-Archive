---
title: "Live USB"
date: 2011-06-03
forum: General Help
---

### Post by Setarkos on 2011-06-03
Hi there
I would like to make a bootable liveUSB of Ubuntu 11 or Mint 10 so that it can run ClamTK. Can anyone helo or point me in the right direction. I was told I need a USB-Stick to do that as ClamTK will need some space to write on.
Cheers!

---

### Post by linuxinstalledfromhdd on 2011-06-03
What system do you want to build it with? Windows or Ubuntu or Mac?

---

### Post by ruffEdgz on 2011-06-03
If you want Ubuntu 11, you will want to go to this page:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

From there, go to 2), select USB Stick and select the type of computer you will be creating it with, then press the "Show me how" button.

This should be able to help you!

---

### Post by Setarkos on 2011-06-03
> **ruffEdgz said:**
> If you want Ubuntu 11, you will want to go to this page:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

From there, go to 2), select USB Stick and select the type of computer you will be creating it with, then press the "Show me how" button.

This should be able to help you!

Thanks, will that create a LiveUSB wit hwhich I can run ClamTK properly?

---

### Post by linuxinstalledfromhdd on 2011-06-03
I think you want something with "persistence".  The only time I have been able to successfully make a USB Flash Drive running Ubuntu with "persistence", was from an installed Ubuntu on a hard drive.   You would simply download an ISO of Ubuntu and use the Startup Disk Creator, and use the slider to add memory to the drive so any changes, or installations you make to the USB are saved to the USB Ubuntu system for next time.

Create the USB Ubuntu Flash Drive system in Startup Disc Creator, and then boot from it, and then install whatever you want.

---

### Post by ruffEdgz on 2011-06-03
> **Setarkos said:**
> Thanks, will that create a LiveUSB wit hwhich I can run ClamTK properly?

Sorry, I placed the LiveCD link. You will want the non Live CD one:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Do the same thing I placed above and this time, it will show you how to install Ubuntu onto a usb which then you should be able to setup ClamTK.

---

### Post by linuxinstalledfromhdd on 2011-06-03
Will that create a persistent Live USB Flash Ubuntu system to install software once the user boots into that device from USB?

---

### Post by Setarkos on 2011-06-03
> **ruffEdgz said:**
> Sorry, I placed the LiveCD link. You will want the non Live CD one:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Do the same thing I placed above and this time, it will show you how to install Ubuntu onto a usb which then you should be able to setup ClamTK.
 
Thanks for your help but now you have posted the same link twice...

---

### Post by ruffEdgz on 2011-06-03
> **linuxinstalledfromhdd said:**
> Will that create a persistent Live USB Flash Ubuntu system to install software once the user boots into that device from USB?

That time I did it, I was able to use it as my portable OS, install applications on the fly and use the resources from the PC for everything else. 

I can just double check this again but that is what the reserved extra space is for and why you should probably have a 10GB or larger usb when you do this.

Will get back to you ASAP.

---

### Post by ruffEdgz on 2011-06-03
@linuxinstalledfromhdd

So I thought I used the Ubuntu.com way to get this to work but I was wrong. That installation to a usb is for the Live CD only.

But I did find an entry on the Ubuntu Wiki about persistent installation if you could guess :P

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I am going to try Method 1 sometime today to make sure that one works but it there are a few options to choose from.

Sorry for the confusion :(

---

### Post by linuxinstalledfromhdd on 2011-06-03
Well I was only asking the user to find out if they wanted something that was persistent or non-persistent.  Sometimes its a pain to have to reinstall something like an antivirus application each time you need it just like we have to do on a live cd.

---

### Post by Setarkos on 2011-06-03
> **ruffEdgz said:**
> @linuxinstalledfromhdd

So I thought I used the Ubuntu.com way to get this to work but I was wrong. That installation to a usb is for the Live CD only.

But I did find an entry on the Ubuntu Wiki about persistent installation if you could guess :P

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I am going to try Method 1 sometime today to make sure that one works but it there are a few options to choose from.

Sorry for the confusion :(

Okay thanks. Should this be possible to create with Fedora 12? Or can could I create the USB-Stick witch a regular Ubuntu Live-CD as long as I download the iso first to a location that I can access with the livecd?
Edit: Just saw the portable linux section, guess it should work with that...
Edit2: Sorry the site confuses me. Which of the methods would be most suitable for my situation? Creating a LiveUSB in Fedora 12 to run ClamTK in Ubuntu 11. Can I just run "portable linux" and that's it?
Edit3: What do you think of this? [http://www.pendrivelinux.com](http://www.pendrivelinux.com)

---

