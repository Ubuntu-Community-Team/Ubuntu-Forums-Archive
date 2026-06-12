---
title: "sdhc not working , ubuntu 9.04"
date: 2009-07-07
forum: General Help
---

### Post by Chris281287 on 2009-07-07
hi, sorry i am a bit of a noob but i cannot get my 4gb panasonic sdhc card to work in my 9.04 install 2gb car works fine same brand.

i have all my differnt card slots in computer:/// but nothing happens when i plug it in i did an  sudo fdisk -1 when i plugged the card in and couldnt see it in the output ....

someone please help.

---

### Post by danwood76 on 2009-07-07
Plug the card in and immediatly run the following two commands from a terminal and post the output:

```

dmesg | tail
lsusb

```

Are you sure the card reader supports sdhc?
I use SDHC all the time in my Ubuntu with no issues.

---

### Post by Chris281287 on 2009-07-08
chris@chrispc-desktop:~$ dmesg | tail
[   11.364384] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   11.364430] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   11.422411] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   11.422464] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   12.066574] ppdev: user-space parallel port driver
[   15.992799] r8169: eth0: link up
[   15.992812] r8169: eth0: link up
[   26.324006] eth0: no IPv6 routers present
[ 1035.077516] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[ 1045.352516] usb 4-1: reset full speed USB device using uhci_hcd and address 2
chris@chrispc-desktop:~$ lsusb
Bus 002 Device 003: ID 0c45:6300 Microdia 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 046d:c227 Logitech, Inc. 
Bus 005 Device 004: ID 1532:000c Razer USA, Ltd 
Bus 005 Device 003: ID 046d:c226 Logitech, Inc. 
Bus 005 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chris@chrispc-desktop:~$

---

### Post by sedawk on 2009-07-08
I agree with the first reply - as far as I understood SDHC cards
need to be supported by your SD card reader. It is very likely
this is a hardware issue, not a driver issue in Ubuntu.

---

### Post by Chris281287 on 2009-07-08
i know my card reader can do it works fine when i boot into xp.

---

### Post by danwood76 on 2009-07-08
Its not detecting if the card has been inserted and the kernel isnt doing anything.

I was reading a post on another forum and he could only use his card reader (same as yours) by plugging the card in first and then the USB.

Could you do that and repeat the commands I posted?

So remove the card reader, insert the card, plug in the card reader and run the two commands and post output.

---

### Post by Chris281287 on 2009-07-09
um its an internal card reader so just unplug it from mobo or ??? 
ill be able to do it when i get home to my PC in a few hours ..

---

### Post by danwood76 on 2009-07-09
Sorry didnt realise it was internal.
If you arent computer savvy I wouldnt bother. It will be plugged in to a motherboard header with a 9 pin socket as opposed to a USB but it will act the same as USB.

The alternative is to switch the computer off and insert the card and see if the sdhc loads on boot.

---

### Post by Chris281287 on 2009-07-09
oh i can do that in an hour when i get home , unplug it from my mobo and reconnect it thats a 10 sec job.
when i leave the card in and try to boot it hangs on my motherboard screen 

i have to take out the card and restart my machine its allways done that doesnt like booting with any sd card left in it.

but i will follow your advise once home .

thankyou for your help so far ...

---

