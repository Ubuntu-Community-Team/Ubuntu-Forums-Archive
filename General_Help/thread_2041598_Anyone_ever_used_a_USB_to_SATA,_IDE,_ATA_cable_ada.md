---
title: "Anyone ever used a USB to SATA, IDE, ATA cable adapter?"
date: 2012-08-12
forum: General Help
---

### Post by sofasurfer on 2012-08-12
I purchased one of these at [http://www.ebay.com/itm/Brand-New-USB-2-0-to-IDE-SATA-5-25-S-ATA-2-5-3-5-Adapter-Cable-fa-/221100435775?pt=US_Drive_Cables_dapters&hash=item337a9ce93f](http://www.ebay.com/itm/Brand-New-USB-2-0-to-IDE-SATA-5-25-S-ATA-2-5-3-5-Adapter-Cable-fa-/221100435775?pt=US_Drive_Cables_dapters&hash=item337a9ce93f) \\:D/

I hooked it up and it recognized my hard drive that I had hooked up to it. I was able to view the files on it.=D>

After a while the drive would not be recognized. Then it was. Now it is not recognized again and I can not figure out why.](*,)

The USB ports recognized thumb drives and mp3 players. I can feel the drive spinning. So, what could be the problem? I assume it must be in the adapter itself, or could I be wrong? I hope someone familiar with this can ask me some questions or give me some suggestions that may help get this thing working again.:?:

I'll be right here waiting :popcorn:

---

### Post by zero2xiii on 2012-08-13
Hay,

The first thing that pops into my mind is POWER.

Once you start having a lot of usb stuff drawing current, some systems tend to overload and thus the drive will be unable to function. This varies on the chip of the usbhost.

Also, while the drive is plugged in, try running lsusb in terminal to see if it is listed. And also keep an eye on the output of dmesg while plugging the drive in and out to see if any errors pop up..

Cherz :)

---

### Post by TheFu on 2012-08-13
I've had an issue with vibrations causing USB devices to disconnect/reconnect over and over. In the end, I moved that device to a different PC, but I probably could have better isolated the connection so vibration wasn't an issue.

For the specific type of device, I've also had issues where they stopped working. I figured it was due to cheap build of the electronics inside. I ended up switching to a Dock-style solution with USB3 and eSATA ports.

The power idea from zer2xii is good too, but I suspect the HDD is getting power directly from a separate power plug, not over USB, right?  You might try using a different USB port - if you are on the front, try a back port or vice versa. They may use different power draws internally.  A powered USB hub might help too, if power really is the issue.

---

### Post by sofasurfer on 2012-08-13
So far I figured out, from someones post on the internet, that you need to plug in the power cable, power up the pc, and after spinup THEN plug in the USB cable. So far it works.

---

