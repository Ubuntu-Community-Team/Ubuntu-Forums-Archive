---
title: "Resized casper-rw file; free space in home folder unchanged?"
date: 2009-11-19
forum: General Help
---

### Post by DColber on 2009-11-19
Problem related to this [html]http://ubuntuforums.org/showthread.php?t=1147101[/html] thread.

I have created a bootable Kubuntu 8.10 on a 4Gb usb stick from a live CD.  I have installed a few packages already, and want to install another, very large package (CCP4 software for crystallography).

Having run out of space after a) downloading, and then b) unpacking, the install fails.  

So using 
*dd if=/dev/zero bs=1M count=500 >> casper-rw*
and
*resize2fs casper-rw*
I resized the casper-rw file from 1.5 to 2.3Gb, as seen in the file's properties.

Unfortunately when I boot from the usb, the free space has not changed.  I have 883 Mb out of 1.5Gb in the home folder (and 810Mb remaining on the usb flash drive).

Can anyone tell me where the extra ~1Gb I added to the casper file, has gone?

Many thanks for your help.

---

