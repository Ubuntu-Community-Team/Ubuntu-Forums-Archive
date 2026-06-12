---
title: "NVidia GTX 550 Ti dual monitors not working."
date: 2011-07-24
forum: General Help
---

### Post by jcd29 on 2011-07-24
I have a Gigabyte GTX 550 Ti card. It has two DVI slots and one mini-HDMI port. 

I use the DVI port with my monitor, and wanted to try to use the HDMI with my TV. So I connected it, but no image appeared. Weird, I thought. So I rebooted and logged on to both Windows and Ubuntu, and yet the only screen with an image was my monitor. I turned the PC off, disconnected the DVI cable, leaving only the TV connected to the HDMI port. Turned the PC on and there we go! I had an image. 

Then when I was done I wanted to go back to my monitor so I connected the DVI cable back to the DVI port, but nope, no image. Had to again reboot and disconnect the HDMI cable for it to work. 

How can I get them to work at the same time? 

Or at least be able to switch between them without rebooting?

---

### Post by der- on 2011-10-31
hi

i do have the same problem:

i use  Kubuntu (10.04) and i bought the gtx550ti and wanted to connect my TV with hdmi.

i found some post ( [http://ubuntuforums.org/showthread.php?t=1780211](http://ubuntuforums.org/showthread.php?t=1780211) ) where it is recommended to use PPA / 
**3rd Party Repository: Ubuntu-x-swat.**


> To install this PPA: 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates  sudo apt-get update sudo apt-get install **[nvidia-settings]("http://www.ubuntuupdates.org/packages/show/247560")** 

i`m going to try this method, 
after finding out jockey isnt function properly and installing the latest driver >nvidia-current< 
crashes my xserver..:(

---

