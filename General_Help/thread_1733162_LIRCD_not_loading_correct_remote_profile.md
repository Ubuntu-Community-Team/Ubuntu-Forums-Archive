---
title: "LIRCD not loading correct remote profile"
date: 2011-04-18
forum: General Help
---

### Post by Kr0nZ on 2011-04-18
Hi, My mce remote had been working fine with lircd for the past 3 weeks or so
when I would run irw i would get lines like :
```
000000037ff07bd9 00 Guide mceusb
000000037ff07bde 01 Right mceusb
```
using mceusb my remote worked perfectly

But when I came home one day the IR receiver light was on constantly and would respond to any input from my remote,
to get any kind of response from it I had to kill lircd unplug the receiver, then replug it and restart LIRCD.

After doing that my remote would only half work, and running irw again instead of getting mceusb I get lines like:
```
000000037ff0ebe1 00 Up vista_mce
000000037ff0ebe1 00 Up_UP vista_mce
000000037ff06bde 00 Right vista_mce
000000037ff06bde 00 Right_UP vista_mce
```
 

So for some reason my remote is being detected as vista_mce, instead of mceusb like it was before when working fine.

Is there any way to force lircd to use mceusb instead of vista_mce?
or is there any other way to fix this?
Thanks for any help

---

### Post by Kr0nZ on 2011-04-19
no-one knows how to force my remote as mceusb instead of vista_mce?

---

### Post by Kr0nZ on 2011-04-19
Heres the output from dmesg | grep lirc
```
[   16.423007] lirc_dev: IR Remote Control driver registered, major 61
[   16.424195] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   16.424198] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   16.424239] usbcore: registered new interface driver lirc_mceusb
[  167.371979] lirc_dev: lirc_register_driver: sample_rate: 0
[  167.377921] lirc_mceusb[2]: Formosa21 eHome Infrared Transceiver on usb3:2

```

Let me know what other information I should provide

---

### Post by Kr0nZ on 2011-04-21
i had just completed a reinstall of the OS(i needed to reorganize my partition's anyway, plus the kernel crashed and couldnt boot anymore), but when i was setting up lircd the FIRST time i had to add lirc_ to mceusb on the REMOTE_MODULES line of hardware.conf to get the remote to work, but this time i didnt need to add lirc_ to mceusb on the REMOTE_MODULES line, but the remote still shows as vista_mce in irw, it behaves REALLY slow and the OK button doesnt work.

Yeh so even a OS reinstall couldn't fix the remote, im not sure what else to do

---

### Post by lsmobrian on 2011-04-22
I'm having some trouble too, though not using Ubuntu (Arch Linux), but hopefully this will help.

First off, check your lirc config file
/etc/lirc/lircd.conf

See if it even has a section for mceusb.  Compare with the mceusb conf distributed with lirc.

The original one from lirc can be found at
/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb 


Best option in my opinion is running: 
```
sudo cp /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb /etc/lirc/lircd.conf
sudo service lirc restart
```

This file has the conf for mceusb, mceusb_hauppauge, and vista_mce.  If it continues to default as vista_mce I suggest deleting the section for vista_mce and restart lircd (sudo service lirc restart).


EDIT:  Like I said, I'm not using this on Ubuntu, so hopefully this does help a little, but it looks like a lot of stuff is set in /etc/lirc/hardware.conf  And I dont have that file on my Arch setup... 
```
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
```

So maybe backup

---

