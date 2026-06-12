---
title: "&quot;File is broken&quot; messages when creating USB drive"
date: 2010-05-27
forum: General Help
---

### Post by gawain2 on 2010-05-27
Hello everyone,

I'm a newbie and am trying to trial Ubuntu 10.04 for the first time on my Dell Inspiron 6000 laptop. When I try to create a USB drive, I get a diagnostic message reading that some files are broken. The first time I ignored it and tried to boot Ubuntu from my USB stick anyway, but I couldn't get further than Ubuntu's boot screen. I tried to access the help menu from the boot screen and it said I was missing the kernel (named "casper" something or other). 

Here's an image of the error message:

[IMG]http://i209.photobucket.com/albums/bb244/Tristam222/errormessage4.png[/IMG]

I apologize for my ignorance and help is much appreciated!

---

### Post by ajgreeny on 2010-05-27
Perhaps the iso file you used to try to make the USB is corrupt.  You can check it in windows somehow, but I'm not sure how, or you can do it in ubuntu if you have a live CD, by booting the CD, finding the folder where the .iso is and running ```
md5sum filename.iso
``` and comparing the output string with that which you can find at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

