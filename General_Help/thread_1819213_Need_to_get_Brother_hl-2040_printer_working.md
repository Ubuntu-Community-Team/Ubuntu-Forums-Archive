---
title: "Need to get Brother hl-2040 printer working"
date: 2011-08-05
forum: General Help
---

### Post by pottzie on 2011-08-05
I'm trying to get a Brother HL-2040 printer working, without much success. I installed the brother-cups driver, but that didn't work. When I try to print, the printer just shoots out blank pages, and the only way I can stop it is by unplugging the printer.
 Worked OK on Ubuntu 10.10. I have gnome fallback, if that matters. There's a post saying that I need to download a ppd file,
[http://ubuntuforums.org/showthread.php?t=1779911](http://ubuntuforums.org/showthread.php?t=1779911)
 but when I try to get it, it opens a page instead of downloading a file. Also the information is from 2008, and I don't know how well that will work with all the changes that have been made to Ubuntu and the newer kernel.

 Hey, I got lucky! went to:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2040](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2040)
 and got the .deb files for the lpr driver and the cups driver. Had to use sudo dpkg -i in the terminal, as I couldn't get the software GUI to work. But it prints, so I'm marking this solved.

---

### Post by Buster95 on 2011-08-13
I had the same experience but got lost with the terminal commands on where to put the downloaded ppd file so that the printer picks it up.

What were the specific terminal commands you used to achieve this? Did you create a directory for "Brother" in the usr/share/ppd folder?

Thanks

---

