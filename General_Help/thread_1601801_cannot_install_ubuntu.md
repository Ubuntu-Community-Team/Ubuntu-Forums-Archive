---
title: "cannot install ubuntu"
date: 2010-10-20
forum: General Help
---

### Post by yeyger on 2010-10-20
i have a gateway mx3215 with the hdd wiped clean.  tried installing ubuntu 10.10 but only get this message

**b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found **


also tells me to go to some website to download drivers.  after the error message, the install seems to proceed but only to freeze after a few minutes.  what to do?  thanks in advance.

btw, i posted this earlier but can't seem to find it.

---

### Post by P4man on 2010-10-20
sounds like 2 unrelated issues. The first one isnt even a real issue; its exactly what the message says, the firmware for your broadcom wireless card is not installed, because ubuntu is not allowed to distribute it. YOu have to fetch it manually from linuxwireless, or semi automatically by running

```
sudo apt-get install b43-fwcutter
```

if you can plug in an ethernet cable to get online. More info here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)

But not having that would just prevent your wifi from working, it should not cause any other issues. At what stage does the install freeze? Are mouse and keyboard still functional? Can you plug in an ethernet cable during the install to see if that helps?

---

### Post by yeyger on 2010-10-20
thanks for replying.  aha.  you're saying i can just ignore the message and download the driver later?  i tried plugging in the ethernet cable coz i read that somewhere but no dice.  about 2 minutes after i get the lengthy b43 driver error message the install seems to proceed bec. the cf reader or cd drive (tried both) will blink.  but after a few minutes everything stops.  they keyboard and mouse will stop working also and the blank screen will eventually turn off.  i sat and waited coz i thought maybe i got timed out of a prompt or something and i even left it on overnight but nothing.  it just freezes a few minutes after i get the error message.  any ideas?  thanks again.

---

### Post by P4man on 2010-10-21
Can you use the livecd without it locking up? 

How much RAM do you have? I googled your notebook type and found by default it ships with just 256 Mb RAM. If yours doesnt have more than that, then you need the [alternate]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") cd to install ubuntu. And frankly, you probably want a more lightweight variant like lubuntu or peppermint os.

If you have 512 MB or more, a few more things to check: in system > administration > disk utility, verify the smart status of the harddisk. Is it healthy? Have you checked the CD or USB for defects? You can do so in the menu that comes up if you press a key at the beginning of the boot process where you see the keyboard logo at the bottom of the screen.

---

