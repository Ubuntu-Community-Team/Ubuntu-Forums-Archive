---
title: "Using Nokia PC Suite on Ubuntu (with QEmu)"
date: 2011-08-09
forum: General Help
---

### Post by wirespot on 2011-08-09
Opening this thread to let others know how to do this.

The point: using a Nokia mobile phone with Nokia PC Suite on Ubuntu.

Phone: Nokia 2730 classic
Ubuntu: Lucid Lynx 10.04 LTS
Connection: micro-USB cable
Software: Nokia PC Suite 7.1, QEmu 0.12.3

1. Install a Windows XP image in QEmu. I won't explain how to do that because that's beyond the point of this tutorial.

2. Connect your phone to the PC through the cable and try all the connection modes (for 2730 there's 3 modes: "PC Suite", "Pictures & Media", and "Data storage". You can use the Settings/Connectivity to make the phone ask which mode to use upon every cable plug. After each connection, run `lsusb` in a console and write down the vendor and device ID next to "Nokia phone". For the 2730 I got 0421:02ba, 0421:02bb and 0421:02b9 respectivelly for the the 3 modes.

3. Run qemu as root and tell it about all the vendor:device pairs you found:

```
sudo qemu -enable-kvm \
-usb \
-usbdevice host:0421:02ba \
-usbdevice host:0421:02bb \
-usbdevice host:0421:02b9 \
-hda /path/to/your/winxp/image
```

The -enable-kvm switch is only appropriate if your CPU supports KVM. It will greatly improve the performance if it's available. Try with and without.

4. Once inside Windows, download and install PC Suite 7.1, then connect the phone in PC Suite mode. It should detect it and start downloading and enabling specific drivers. If all went ok the phone icon on the tray should have a green dot and when you click on it you get the PC Suite working. The phone should show after a few seconds by itself inside the Suite, no need to connect it manually.

5. Troubleshooting: if you're being told the phone is in an "un-compatible connection mode" then make sure it's in PC Suite mode. If it insists on saying that, reboot the Windows environment and/or reconnect the phone. Sometimes it doesn't download all the drivers on the 1st try and you have to let it try again a couple of times.

YMMV, worksforme etc. :) Afraid can't help you with your own phones, this is how it (eventually) worked for me.

---

### Post by Kira_Belka on 2011-08-09
How about "Gnocky"? "gnokii" and "wammu" ?

---

### Post by Kira_Belka on 2011-08-09
and I used Nokia PC suite (sorry I don't remember version) under Virtual Box .. and no problem at all.. it was VBox 4.02 + extenson pack certainly

---

### Post by Duncan Williams on 2011-08-09
HI THERE GUYS,
just had a look at wammu (installed and tried it).
It doesn't support my phone. (looks like just what I need though)

Anyone know how I can access my `samsung C5220'
I can and am using it as a modem.
I would like to use sms and transfer files to and from 
the 2gig micro-sd card. (I know I can use a card reader)

---

### Post by wirespot on 2011-08-10
[quote=Kira_Belka]How about "Gnocky"? "gnokii" and "wammu" ?[/quote]

They are outdated and shoddy. They work or not work randomly. And wammu can only read stuff from the phone, it can't put it back, so... ok, having a backup is better than nothing but I don't look forward to re-entering my contacts or calendar entries by hand.

I've also tried SyncEvolution (sync-ui). It has a lot of promise since it's based on OBEX, which lots of phones support. It sort of worked (both ways) for a while, if you didn't mind that it messed up the calendar entries (shifted by a few hours and made duplicates). Lately it stopped working (hangs forever while connecting).

I won't even go into actually integrating the contacts and calendar with any other piece of software (email, organizer etc.) because there's very little of that. Evolution and SyncEvolution are pretty much the only game in town.

In all fairness, Nokia PC Suite is not all that good either. I've moved some messages around the folders and now it shows something completely different in the Suite from what's actually on the phone, and I can't get it to fix that. So if Nokia themselves can't seem to be able to make software that works with their own phones, what can you expect from 3rd party hackers. :)

I might have to try the Ovi suite, maybe that one is better. :/

The best solution for backups I found, if the phone supports it: the phone itself has a feature of packing up settings, contacts, calendar and messages in a single file on the SD card. You simply save that file on your PC or wherever you want, and later on if you replace the phone it can restore stuff from that file.

---

