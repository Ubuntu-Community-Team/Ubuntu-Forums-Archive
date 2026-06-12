---
title: "Vodafone Mobile Connect"
date: 2006-05-15
forum: General Help
---

### Post by simo on 2006-05-15
I'm tired of this vodafone umts/gprs card. I cant get it working.
I red tons and tons of forums topics and various howtos but it seems to me that i could get it working if someone tells me why i cant have logs like everybody else.
Well, I mean when I type dmesg I do not have messages like registering generic usb serial etc.
I managed to get it by typing 
                  sudo modprobe serial_cs
                           and
                  sudo modprobe usbserial vendor=0x0af0 product=0x5000
but nothing is connectid to /dev/ttyUSB0 or 1,2. I looked for it but it is not there so I maked it
                  mknod /dev/ttyUSB0 c 188 0
                  mknod /dev/ttyUSB1 c 188 1
                  mknod /dev/ttyUSB2 c 188 2
and after I replug the card nothing new happens.
I had the same problem on Fedora 4 so tried download in new kernel 2.6.16 and compiling it, but nothig seems to work.

Please if somebody can give me some tips i would be greatful.I'm tired of holding winodowz only for porpuses of internet.

---

