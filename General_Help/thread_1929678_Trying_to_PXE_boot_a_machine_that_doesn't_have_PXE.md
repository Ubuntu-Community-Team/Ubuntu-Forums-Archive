---
title: "Trying to PXE boot a machine that doesn't have PXE available in BIOS"
date: 2012-02-22
forum: General Help
---

### Post by cptrohn on 2012-02-22
The machine is the ASUS Zenbook and the customer wants to tun a dualboot setup with Windows 7 Pro and Ubuntu, problem is their is a need to PXE boot into a Windows domain.. and there is no PXE setting in the BIOS of the machine.

So I was researching gPXE, and was researching LINBO as possible solutions but was wondering if anybody else had ran into this problem and what possible work-arounds had worked for them?

---

### Post by roelforg on 2012-02-22
Etherboot (gPXE) (etherboot.org) should do the trick.
You can run it from an usb,cd,hdd or flash it to your nic.

---

### Post by cptrohn on 2012-02-22
> **roelforg said:**
> Etherboot (gPXE) (etherboot.org) should do the trick.
You can run it from an usb,cd,hdd or flash it to your nic.

Thats what I was thinking as well... Now, is it possible to keep a back up of the factory firmware for the NIC in case something goes wrong so I don't brick a $1200 notebook? LOL

---

### Post by roelforg on 2012-02-22
> **cptrohn said:**
> Thats what I was thinking as well... Now, is it possible to keep a back up of the factory firmware for the NIC in case something goes wrong so I don't brick a $1200 notebook? LOL

First create a nic rom using this site: [http://rom-o-matic.net/gpxe/gpxe-1.0.1/contrib/rom-o-matic/](http://rom-o-matic.net/gpxe/gpxe-1.0.1/contrib/rom-o-matic/)
And now follow the instruction here: [http://etherboot.org/wiki/romburning](http://etherboot.org/wiki/romburning)
Note: skip the build-rom step in the etherboot wiki, use the rom created with the first site.
Recovering from errors is also on the wiki.

WARNING: When done improperly, your NIC may get corrupted. (mandatory warning)

---

### Post by cptrohn on 2012-02-22
> **roelforg said:**
> First create a nic rom using this site: [http://rom-o-matic.net/gpxe/gpxe-1.0.1/contrib/rom-o-matic/](http://rom-o-matic.net/gpxe/gpxe-1.0.1/contrib/rom-o-matic/)
And now follow the instruction here: [http://etherboot.org/wiki/romburning](http://etherboot.org/wiki/romburning)
Note: skip the build-rom step in the etherboot wiki, use the rom created with the first site.
Recovering from errors is also on the wiki.

WARNING: When done improperly, your NIC may get corrupted. (mandatory warning)

Thanks, yes thats the same documentation that I was seeing as well.  Wish me luck!  I might end up with a $1200 paperweight!

---

### Post by roelforg on 2012-02-22
> **cptrohn said:**
> Thanks, yes thats the same documentation that I was seeing as well.  Wish me luck!  I might end up with a $1200 paperweight!
Hence the warning.

Did it once myself though, it's not too hard.

---

### Post by cptrohn on 2012-03-01
OK, just some information so that it might help folks out in the future...

On the ASUS Zenbook it uses USB ethernet... Soooo  to be able to get to the PXE boot option you have to have the USB ethernet adapter plugged into a USB port with an active network connection to get the PXE option to show up in the BIOS.  Not sure if this is the case with all the new ultrabooks out there... but just something to check if anybody else runs across this issue..

---

### Post by Delphinus on 2012-03-13
> **cptrohn said:**
> OK, just some information so that it might help folks out in the future...

On the ASUS Zenbook it uses USB ethernet... Soooo  to be able to get to the PXE boot option you have to have the USB ethernet adapter plugged into a USB port with an active network connection to get the PXE option to show up in the BIOS.  Not sure if this is the case with all the new ultrabooks out there... but just something to check if anybody else runs across this issue..

Thankyou very much! I scoured the bios with no PXE options, and then realised I had the USB Ethernet plugged into the USB3 port on the right side of the zenbook. Once I used the USB 2.0 port on the left, the PXE Boot options were available in bios to be enabled. Thankyou!

---

