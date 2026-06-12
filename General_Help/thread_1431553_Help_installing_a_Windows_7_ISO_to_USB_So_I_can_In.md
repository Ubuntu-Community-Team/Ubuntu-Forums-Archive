---
title: "Help installing a Windows 7 ISO to USB So I can Install on another hd."
date: 2010-03-16
forum: General Help
---

### Post by xXBinaryXx on 2010-03-16
I have a Windows 7 .iso file on my computer but how can I put it on my flash drive so that way I can boot from it and install it on another hard drive that I have? I am currently running Ubuntu 9.10.

---

### Post by Nostalos on 2010-03-16
Unfortunatly you can't do it purely from Ubuntu.  Well you could, if you had access to a windows 7 system to copy the boot block.  But if you could do that you would just use that box to make ISO to USB conversion anyway.

[http://download.cnet.com/Windows-7-USB-DVD-Download-Tool/3010-18513_4-11115251.html](http://download.cnet.com/Windows-7-USB-DVD-Download-Tool/3010-18513_4-11115251.html)

Other Options are to boot from a Vista DVD as its the same bootsector for Vist as Win 7.


Quick run down.  USB has to be formatted NTFS and set the partition as bootable.  Copy the contents of the extract the contents of the ISO using 7-zip or loop mount over to the USB formatted NTFS.   Then the hard part is getting the boot sector.  You will either need a working Vista/Win7 machine to execute the command in the boot folder

bootsect /nt60 c:

where C: is the usb Drive you are wanting to make bootable.

As I said. its the same for windows 7 as Vista and you can follow this howto.

[http://kmwoley.com/blog/?p=345](http://kmwoley.com/blog/?p=345)

---

