---
title: "Downloading images from Sony Ericsson K750i"
date: 2009-11-21
forum: General Help
---

### Post by chandra on 2009-11-21
I have a Sony Ericsson K750i mobile phone from which I want to download images.

In the past, this device was recognized as a USB mass storage device and I could easily download images. That is now not possible.

My current setup is a desktop PC without bluetooth connectivity running Kubuntu Karmic.

I have tried wammu: the phone is recognized and I can see folders, such as Calendar, Calls, Messages, etc., but not the Pictures folder. The phone is recognized as a Sony Ericsson K750i/750c and is connected as /dev/ttyACM0 using at19200 as connection mode. This is I believe a modem connection.

I have tried to get to the USB mass storage by using bitpim. I have added the file /etc/udev/rules.d/75-mobile-phone.rules```
#
# See http://www.bitpim.org/help/ under Linux USB setup
#
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="mobile_phone_rules_end"

# Sony Ericsson K750i mobile phone
SYSFS{idVendor}=="0fce", SYSFS{idProduct}=="d016", GROUP="dialout", MODE="0660"

LABEL="mobile_phone_rules_end"
```
but am still unable to use the mass storage on the mobile phone.

```
lsusb
``` shows the mobile phone being recognized with the line ```
Bus 006 Device 002: ID 0fce:d016 Sony Ericsson Mobile Communications AB K750i Phone
``` but it appears that the port is not accessible. A screenshot of the ports as put out by bitpim is attached.

```
dmesg
``` gives a tail message like```
[ 2712.754399] usb 6-2: usbfs: interface 1 claimed by cdc_acm while 'python' sets config #1
```

Can someone help me get the images off this mobile phone please?

I would like to avoid doing this using VirtualBox unless I have to.

Many thanks.

---

### Post by llamabr on 2009-11-21
does it actually mount?  What's the output of 

```
df
```

---

### Post by chandra on 2009-11-21
No, it does not get mounted and is not shown in either 
```
df
``` or in ```
mount
```.

---

### Post by chandra on 2009-11-21
Here is what I did to get around the problem:

1. sudo apt-get install usbmount pmount

2. Create /etc/udev/rules.d/75-mobile-phone.rules with this content:

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="mobile_phone_rules_end"

# Sony Ericsson K750i mobile phone
SYSFS{idVendor}=="0fce", SYSFS{idProduct}=="d016", GROUP="plugdev", MODE="0660"

LABEL="mobile_phone_rules_end"

3. Check that dmesg | tail had something like this:

[ 9833.932132] scsi 15:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[ 9833.933302] sd 15:0:0:0: Attached scsi generic sg3 type 0
[ 9833.972064] sd 15:0:0:0: [sdc] 124416 512-byte logical blocks: (63.7 MB/60.7 MiB)
[ 9833.982224] sd 15:0:0:0: [sdc] Write Protect is off
[ 9833.982235] sd 15:0:0:0: [sdc] Mode Sense: 00 6a 00 00
[ 9833.982242] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 9834.015020] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 9834.015029]  sdc: sdc1
[ 9834.055064] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 9834.055076] sd 15:0:0:0: [sdc] Attached SCSI removable disk

4. pmount /dev/sdc1 /media/usb0

5. cd /media/usb0

to access the mobile phone as a mass storage device.

6. cd ~/; pumount /media/usb0

to unmount the device.

This workaround was suggested by

[http://ubuntuforums.org/showpost.php?p=6204815&postcount=13](http://ubuntuforums.org/showpost.php?p=6204815&postcount=13)

I do not understand the intricacies of how this works or whether it will always work, but it enabled me to download the images from my mobile phone in Karmic, something that I was able to do in previous releases but not in Karmic.

See also

[https://bugs.launchpad.net/ubuntu/+bug/368053/comments/5](https://bugs.launchpad.net/ubuntu/+bug/368053/comments/5)

---

