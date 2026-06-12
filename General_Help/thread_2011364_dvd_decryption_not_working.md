---
title: "dvd decryption not working"
date: 2012-06-27
forum: General Help
---

### Post by kjbox on 2012-06-27
I have installed libdvdread4 and libdvdcss2 using the directions on [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/) .

I am still getting a message to say dvd cannot play as it is encrypted and no decryption software is installed.

The above article went on to say the following:

[B]Decryption errors

    If you've installed libdvdcss2 as described above, it should Just Work. However, I had to chmod 660 /dev/sr0; chgrp cdrom /dev/sr0 (replace with the path to your dvd drive) in order to get videos to play. [/B]

Which bit do I chnge to the path to my dvd player? The dvd player is an external drive connected via a USB3 port, how do I get the correct path to it?

Thanks in advance for any help or suggestions.

---

### Post by dino99 on 2012-06-27
into a terminal: sudo lshw

---

### Post by kjbox on 2012-06-27
Thanks for that. I ran lshw and found the dvd info as follows:

  *-scsi:1
          physical id: 2
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             product: SBW-06D2X-U
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/cdrom2
             logical name: /dev/cdrw2
             logical name: /dev/dvd2
             logical name: /dev/dvdrw2
             logical name: /dev/sr0
             version: C701
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc

Which logical name should I use and which bit of the code mentioned in my first post needs to be altered to the new path?

Thanks in advance

---

