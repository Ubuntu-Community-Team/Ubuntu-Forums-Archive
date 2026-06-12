---
title: "imagewriter"
date: 2009-08-04
forum: General Help
---

### Post by rcdavis on 2009-08-04
Having a problem using imagewriter.  It stops after displaying the following and being left for at least 15 minutes without change.:        
                                                      
Image: /home/rcdavis/Download/ubuntu-9.04-netbook-remix-i386(2).img
Target Device: Kingston DataTraveler 2.0 (/dev/sdd)
Unmounting all partitions of /dev/sdd:
Trying to unmount /dev/sdd...
/dev/sdd successfully unmounted

Imagewriter was downloaded and installed using Synaptic. I have un-installed and re-installed several times without this having any effect.

Using Ubuntu 8.04.

---

### Post by BrianCSE on 2009-08-23
did you ever get this resolved? I'm having the same issue

---

### Post by maxpowers43 on 2009-08-26
me too! trying to demo ubuntu to work associate...not looking polished right now..me or ubuntu.

---

### Post by Adam Fitton on 2009-09-17
Yeah I just had the same problem after years!

I think it was from having the Image deep in a file structure. Move the img file closer to root. I put it on my desktop and it worked fine for me then.

---

### Post by sougat818 on 2010-05-22
Placing the file in the desktop worked for me too\\:D/

---

### Post by zenawenliang on 2011-04-10
Thanks this post helped me with Chromium OS, thank guys!

---

### Post by Rebelli0us on 2011-11-10
The file open dialog doesn't work, wherever you navigate to it shows only directories -- NO FILES, so there is seemingly no way to select your ISO file. So I pasted the full path + filename.iso in the text field at the top of the "select image" dialog where it says "location", and it worked. It produced a bootable Linux on the flash drive.

I was using the ImageWriter in the Ubuntu Software Center, other distros have their own ImageWriter. OpenSUSE has a different ImageWriter, so YMMV.

---

### Post by Tuna130 on 2012-07-14
The bug seems to be that there should not be any blank spaces or odd characters in the path to your .img file. After correcting some folder names in my case, it worked fine!

[https://bugs.launchpad.net/usb-imagewriter/+bug/1013834](https://bugs.launchpad.net/usb-imagewriter/+bug/1013834)

PS Alternatively use command line dd command.

---

