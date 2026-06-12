---
title: "Install from SD card"
date: 2010-07-26
forum: General Help
---

### Post by Sly-.- on 2010-07-26
Hey. So I want to install Ubuntu on my netbook, but as it's a netbook, it has no CD/DVD drive. I don't have any USB sticks to hand either. What I do have though, is an SD card and memory card reader (it has a USB connector). So, what I'd like to know is, can I install Ubuntu via this set up? If so, how must I prepare the SD card?

Cheers!

---

### Post by limestone on 2010-07-26
[http://arstechnica.com/hardware/news/2008/07/running-ubuntu-on-the-eee-pc.ars](http://arstechnica.com/hardware/news/2008/07/running-ubuntu-on-the-eee-pc.ars)

---

### Post by snowpine on 2010-07-26
Assuming that your BIOS supports this, the process would be identical to creating a Live USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Shompol on 2010-07-26
1. Install the bootable ISO on SD. 
2. Open BIOS settings and pick SD reader or USB as the promary boot device

Here's where I run into a problem with original 7" ASUS EEE PC:

it would not boot from SD card reader! When I used an external card reader, that plugs into USB, it worked! 

3. Reboot and install.

Also: on the above mentioned machine, the "ubuntu netbook remix" installer froze, and I narrowed down the reason was that the partitioner could not run on 7" screen! 
Standard Ubuntu Desktop distro installed no problem. I had to setup multiple virtual desktops and ctrl-alt-arrow between them because all ubuntu config windows did not fit on a single screen.

---

### Post by C.S.Cameron on 2010-07-26
Probably easiest to use Unetbootin if you currently have Windows on your netbook.

---

