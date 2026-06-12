---
title: "Install Ubuntu Through SD Card?"
date: 2010-06-20
forum: General Help
---

### Post by flying_phoenix on 2010-06-20
Hello I've recently purchased a HP 210 Mini. I've installed Ubuntu Netbook Remix through Wubi but have found to be ridiculously unreliable as the Update Manager always freezes! :mad: 

I've reinstalled 4 times now and still no luck. So I assume that it will be better to install the .iso from the site. However my computer doesn't have a disc drive, so I wonder if there's a way to install Ubuntu from there, I mean it works for a USB drive.

---

### Post by pytheas22 on 2010-06-20
If you have USB ports, you can install Ubuntu using a USB drive.  Check out [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The title of your thread mentions an SD card and I don't think there's any way to install Ubuntu from there, since I don't think you can boot to one (technically you could probably boot to another device, mount the SD drive and run the installer stored on it, but this is way more complicated than you need).  But if you have USB, that should be all you need.

---

### Post by flying_phoenix on 2010-06-20
> **pytheas22 said:**
> If you have USB ports, you can install Ubuntu using a USB drive.  Check out [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The title of your thread mentions an SD card and I don't think there's any way to install Ubuntu from there, since I don't think you can boot to one (technically you could probably boot to another device, mount the SD drive and run the installer stored on it, but this is way more complicated than you need).  But if you have USB, that should be all you need.

Explain the complicated way please since I don't have USB card.

---

### Post by aysiu on 2010-06-20
I have an HP Mini 1120nr, and I have installed Ubuntu through both a USB stick (actually an MP3 player) and an SD Card.

Basically, you download the .iso, then you also download [UNetbootin](http://unetbootin.sourceforge.net), and run it, pointing it to the .iso and your SD Card. (The SD Card *must* first be formatted as FAT32 or FAT16.)

Then, right at the beginning of bootup, press F9 and select to boot from the SD Card.

---

### Post by technocp on 2010-06-20
> **flying_phoenix said:**
> Hello I've recently purchased a HP 210 Mini. I've installed Ubuntu Netbook Remix through Wubi but have found to be ridiculously unreliable as the Update Manager always freezes! :mad: 

I've reinstalled 4 times now and still no luck. So I assume that it will be better to install the .iso from the site. However my computer doesn't have a disc drive, so I wonder if there's a way to install Ubuntu from there, I mean it works for a USB drive.
download the .iso file from where ever is comfortable for you
google for unetbootin and download (it is around 4 mb)
both windows and linux version of unetbootin are available

start unetbootin after install
select the iso file from the browse path option
select the storage type from the option available at bottom

just go thru the process and restart your pc with usb boot option

thats it it will start working with you

---

### Post by pytheas22 on 2010-06-20
> Explain the complicated way please since I don't have USB card. 

The other posters have said pretty much what I would say.

But one larger issue that has just come to mind after rereading your first post is that I wouldn't be so sure that installing from the ISO will solve your problems with Ubuntu Netbook Remix.  Wubi installs all of the same files as the ISO installer; the only difference is that Wubi creates a disk image for Ubuntu within your Windows file system.  It's hard to imagine how this could cause problems with Update Manager.

But, I could be wrong and installing using the ISO might for some strange reason solve the issues you're having.  If not, I'd suggest installing regular Ubuntu, without Netbook Remix.

---

