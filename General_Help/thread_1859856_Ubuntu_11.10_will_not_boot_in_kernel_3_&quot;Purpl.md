---
title: "Ubuntu 11.10 will not boot in kernel 3 &quot;Purple screen&quot;"
date: 2011-10-14
forum: General Help
---

### Post by ZING on 2011-10-14
I freshly installed an unmodified 11.04 and then upgraded to 11.10. I can not boot into the new kernel. I have to select the old one. When trying to boot in the new kernel, I just get a blank purple screen.

lsb_release -a =

Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

I've tried GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" like someone recommended on another post but still have the same problems.

PLEASE someone help me fix this... I need my PC for work and school.

---

### Post by ZING on 2011-10-14
I also tried GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" and get the same thing

---

### Post by collisionystm on 2011-10-14
Are you using an ATI Radeon graphics card?

---

### Post by xaz0r on 2011-10-14
Are you running it in VirtualBox by chance? I had this exact same issue. I booted up into the recovery kernel, opened /var/log/Xorg.0.log and noticed errors about the VBox drivers. I knew this was because the kernel had been updated and I had not yet reinstalled the VirtualBox Guest Additions. So here's what I did to fix it:

1) Boot up to recovery kernel (press escape repeatedly before it boots to get to boot menu) and login with your root password
2) Go to "Devices" -> "Install Guest Additions" in your VirtualBox menu
3) Run the following:

        mount /dev/cdrom /cdrom
        /cdrom/VBoxLinuxAdditions.run
        reboot

---

### Post by TheBleak on 2011-10-14
I think I'm having the same issue but I use VMware... 
Any ideas on what VMware users need to do?

---

### Post by ZING on 2011-10-14
No vm or anything just ubuntu freshly installed. I am using the on board video ati radeon xpress 200 on emachine t3504

---

### Post by collisionystm on 2011-10-14
its the video card driver.

---

### Post by ZING on 2011-10-14
What can I do?

---

### Post by xaz0r on 2011-10-14
> **TheBleak said:**
> I think I'm having the same issue but I use VMware... 
Any ideas on what VMware users need to do?

I'm guessing that you need to reinstall VMware Tools for yours to work. I would start by booting into the recovery console and opening up /var/log/Xorg.0.log and seeing what errors it shows. I haven't used VMware in a long time, so I really couldn't tell you how to install VMware tools, but I'm guessing a quick Google search would do the trick.

---

### Post by ZING on 2011-10-14
> **xaz0r said:**
> I'm guessing that you need to reinstall VMware Tools for yours to work. I would start by booting into the recovery console and opening up /var/log/Xorg.0.log and seeing what errors it shows. I haven't used VMware in a long time, so I really couldn't tell you how to install VMware tools, but I'm guessing a quick Google search would do the trick.

Doesn't let me boot in recovery mode, I have to use the old kernel

---

### Post by xaz0r on 2011-10-14
That should be fine. I did the same. It should show two entries. The first one is to boot normal, the second one says "(Recovery)" at the end. Boot up to that and then just choose the top option, something like "Continue normal boot". You should end up with a command line where you can login and work.

---

### Post by ZING on 2011-10-14
I tried installing VMware still the same problem

---

### Post by xaz0r on 2011-10-14
> **ZING said:**
> I tried installing VMware still the same problem
Just for clarity did you mean VMware? Or VMware Tools in the guest OS?

Did you ever open up /var/log/Xorg.0.log to see what errors it shows?

---

### Post by ZING on 2011-10-14
both, and yes... idk where to find the errors... just endless amount of data in the log file

---

### Post by ZING on 2011-10-14
would a new gfx card fix this? If so what would be a nice cheap one under $50 that would work? I dont play games... I just use it for work, school, and some movies... i do like the 3d effects also

---

### Post by xaz0r on 2011-10-15
> **ZING said:**
> would a new gfx card fix this? If so what would be a nice cheap one under $50 that would work? I dont play games... I just use it for work, school, and some movies... i do like the 3d effects also

You weren't using VMware in the first place right? So none of the information I've given would really apply to you. It should hopefully help TheBleak as he was running VMware.

Your problem is different, but probably also video related. For you, it would really help to find the errors in the Xorg log. For me they were down at the bottom of the file, that's generally where you'll find the errors because it usually stops as soon as it hits a critical error like that. Look at the bottom of your Xorg.0.log and see if you can find some errors about missing modules or failing to load some module(s). Of course, if it is video related then there's probably both a software and hardware solution. You could replace your video card if your looking for an excuse to upgrade :P

---

### Post by effenberg0x0 on 2011-10-15
Try this:

If you're on recovery, you have to run this first:
```
mount -oremount,rw /


```Edit Grub Defaults file:
```
sudo cp /etc/default/grub /etc/default/grub.backup
sudo nano /etc/default/grub

```GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DEFAULT=0

- Eliminate ALL instances of the words "quiet" and "splash"
- All other lines can be commented with "#" in their beginning.

Run this:
[HTML]sudo mv /etc/init/plymouth-splash.conf /etc/init/plymouth-splash.conf.backup
[/HTML]Then update grub:
```
sudo update-grub
```And reboot:
```
sudo reboot now
```Choose the default kernel (not recovery). There are no elements that can activate the purple screen of death now.

Effenberg

---

### Post by philbrown7 on 2011-10-22
I had the same problem. This worked to fix it.
Ubuntu 11.10 is now loading with Kernel 3. Thank you.

---

### Post by philbrown7 on 2011-10-22
I had the same problem. This worked to fix it.
Ubuntu 11.10 is now loading with Kernel 3. Thank you.

---

