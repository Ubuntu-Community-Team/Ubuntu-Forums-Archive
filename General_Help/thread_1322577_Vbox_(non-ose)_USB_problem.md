---
title: "Vbox (non-ose) USB problem"
date: 2009-11-11
forum: General Help
---

### Post by nikola43 on 2009-11-11
I'm running Intrepid 64 bit and installed Ubuntu 9.1 (32-bit) as a guest using VirtualBox 3.0.10r54097. I still can't get the guest to recognize USB drives, although my usb mouse seems to work fine. I finally figured out how to put myself into the vboxuser group and when I rebooted the guest mounted one of the usb devices I had listed in the vbox settings (where I had also listed the mouse), but the mouse went away/locked up/wouldn't respond to the host or the guest. I had installed Guest Additions and it was working fine before all this. I found info on Ubuntu docs site, a partial copy of which follows, that appears to apply to my problem;

"In Intrepid the lines required to mount usbfs have been removed entirely, so you need to add the following lines to /etc/init.d/mountdevsubfs.sh at the end of the do_start() function. Note that this is subtly different than the lines required for Gutsy/Hardy. the arguments for the domount function are slightly different from previous versions.

        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

Then run the script that you just edited:

sudo /etc/init.d/mountdevsubfs.sh start

n order to give users in the vboxusers group write permissions to the devices in /proc/bus/usb, you'll need to edit some rules in /etc/udev/rules.d.

Under Hardy and Intrepid, edit /etc/udev/rules.d/40-basic-permissions.rules to say the following:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Then, restart the udev service:

sudo /etc/init.d/udev restart

Now, if you haven't done it already, make sure your user is part of the group vboxusers using the following command:


sudo usermod -G vboxusers -a `whoami`"

what does all this mean and exactly how do I implement it in the console terminal?

---

### Post by El Zoido on 2009-11-11
Basically this are a couple of scripts you have to edit and then execute via console.

To do this open the files in an editor as root (open a terminal and type):
(Before you do so its probably best to do a backup of the files: sudo cp /etc/init.d/mountdevsubfs.sh /etc/init.d/mountdevsubfs.bak)

sudo gedit /etc/init.d/mountdevsubfs.sh

then copy/paste the lines found on the web to the end of the do_start() function:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Now you save and close gedit and type into the terminal:

sudo /etc/init.d/mountdevsubfs.sh start

Now you do the same to edit the second file (this time it's called /etc/udev/rules.d/40-basic-permissions.rules) and paste the other lines.

Hope that helps!

---

