---
title: "slow boot"
date: 2010-11-07
forum: General Help
---

### Post by browseanddownload on 2010-11-07
My ubuntu(10.10) installation takes a relatively longer time(90 seconds) to boot. I think part of the problem might be related to an error message during boot related to usb drivers. 

```

[    2.717076] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    3.244051] usb 4-2: new full speed USB device using ohci_hcd and address 3
[   12.029046] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed

```I have attached the relevent part of dmesg output also. 

Is this the appropriate forum for me to address this question? If not could you point me to the right place?

-Abhijith

---

### Post by dino99 on 2010-11-07
into a terminal, run:

sudo update-usbids && sudo update-pciids
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by browseanddownload on 2010-11-24
@dino99,

Thanks for the reply. I failed to discover that my question had been answered and hence the delay.

Unfortunately, doing as you suggested(update-usbids, update-pciids) isn't helping. The error message still remains.

What do you suspect the problem to be? A new pci or usb related hardware?

---

### Post by dino99 on 2010-11-25
Looking at dmesg.txt posted above, i see:

- acpi issue ([Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS)
- driver hiddev used (usbcore: registered new interface driver hiddev)

So to have better chances:

with synaptic, check that these packages are installed: read-edid, linux-firmware, usb-modeswitch, usbutils, usbmount.Then install the latest kernel: 2.6.37 from this ppa

--> open synaptic repo tab (third party) and add: ppa:xorg-edgers/ppa ([https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=maverick)), then update, from the new packages, install only the the 2.6.37-6 kernel (source + header + image), when done: deselect the xorg-edgers repo into the synaptic repo tab, and update again.

Then reboot with 2.6.37 and:
- check your keyboard config, be sure to use the good model
- watch logs again
- maybe run again the commands given with my first post.

Hopping that thinks are better now :)

---

### Post by browseanddownload on 2011-04-05
I am noticing your reply now. :-(

I added your specified repository. I notice that 2.6.37-6 kernel is not available as of now. Is it ok if I install the 2.6.38-4?

-Abhijith

---

### Post by browseanddownload on 2011-04-05
By the way I subscribed myself to this thread now( i had failed to find how to do it earlier).

-Abhijith

---

### Post by browseanddownload on 2011-04-05
I upgraded to 2.6.38-4 as instructed.

I ran the commands you gave in the first post.

The delay in boot along with the message in dmesg exists.

Attached is the output of dmesg.

---

