---
title: "Ubuntu 12.04 not seeing memory stick in usb on working Ubuntu"
date: 2012-10-04
forum: General Help
---

### Post by USAGeorge on 2012-10-04
Ubuntu 12.04 not seeing memory stick in usb on working Ubuntu
 Info. I have a Presario c700 with Ubuntu 12.04 only. It worked excellent for a few months and after update problem it developed problems.
 The touchpad pointer froze but I got that fixed from info here. Also the updates were completed. Last week I put the usb stick in to copy and store some files; it is the same one I used to load Ubuntu into the laptop. Nothing happened in that it didn't open,no box,no icon. I looked around here and I'm not sure what to do next. Here is what I know..
1. Did ls media and it sees PENDRIVE when usb stick is in.
 2.Did lsusb and it showed bus 001 device 002 id 0781:5575 Sandisk Corp with usb plugged in.
3. In bios floppy boot is set to Enable.
 Thats where I am,not sure what to check next......
  Any advice would be appreciated.    I'm not that computer slick it took me a while using this forum to get this far....Thank you

---

### Post by windscape on 2012-10-04
Hi,

Since the PENDRIVE shows up in /media, that probably means that it is mounted and ready to use. Try browsing to /media in Nautilus or Thunar or whatever file manager you use and see if you can open the PENDRIVE directory and copy files there.

---

### Post by USAGeorge on 2012-10-04
I'll give it a go,gonna take a while to find the file manager......but still trying to figure why it's not opening. I never used the stick since I put Ubuntu up and am assuming it should give me a image/icon or open on the screen....... Thanks for the advice,,

---

### Post by USAGeorge on 2012-10-04
I opened files and media inside it. I opened the pendrive and can read whats stored on the memory stick........So now? Is there something wrong with automount?
 I'll see if there is any info on how to check how it works....Thanks for the help,,getting a little closer to the problem..

---

### Post by USAGeorge on 2012-10-04
Problem resolved....
used sudo apt-get install dconf-tools
 It noted a missing file and corrected/updated...
on restart of laptop the icon was there and the problem resolved....

 I went there to see if the autoload was unchecked....

---

