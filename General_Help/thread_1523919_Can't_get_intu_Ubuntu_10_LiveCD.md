---
title: "Can't get intu Ubuntu 10 LiveCD"
date: 2010-07-04
forum: General Help
---

### Post by sza on 2010-07-04
Hi all,

It happens only on my LG E310  laptop. in any other computer the CD works fine.

I also checked the CD for defects and it is clean.

when I try to get into the option "try ubuntu without any changes to your computer" the computer is 'thinking' for a couple of minutes and is stopping in the situation in the picture...

Hope someone knows how to fix it... I realy need ubuntu!!!!

---

### Post by jingaling on 2010-07-04
Just as a thought, have you tried making a bootable USB and starting the Live CD from that?

Instructions are here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Just worth a try in case your CD drive is bust or something.

Jing

---

### Post by sza on 2010-07-04
No, I havn't.
But if it was the problem- the computer shouldn't have run ubuntu 8 live cd, and it works fine...

---

### Post by philinux on 2010-07-04
> **sza said:**
> Hi all,

It happens only on my LG E310  laptop. in any other computer the CD works fine.

I also checked the CD for defects and it is clean.

when I try to get into the option "try ubuntu without any changes to your computer" the computer is 'thinking' for a couple of minutes and is stopping in the situation in the picture...

Hope someone knows how to fix it... I realy need ubuntu!!!!

Try the safe graphics option.

---

### Post by sza on 2010-07-04
I can't find that option, where is it?

---

### Post by cent on 2010-07-04
I had a similar problem when i tried 9.10 on my desktop. It appeard to be a defect on the disk I burned as I alredy had 2 failed disk, but the integrety test passed fine. Stragely chosing 'Install Ubuntu' from the bootup menu worked.

---

### Post by philinux on 2010-07-04
> **sza said:**
> I can't find that option, where is it?

Boot the live cd and as soon as the purple screen appears press any key. 

The extra options should be there.

---

### Post by Rubi1200 on 2010-07-04
You could try some of the options mentioned in this post:

[http://ubuntuforums.org/showpost.php?p=9543761&postcount=2](http://ubuntuforums.org/showpost.php?p=9543761&postcount=2)

To change boot parameters on the LiveCD:

After choosing the option to try hit F6 then Esc to see this:

[B]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

[/B]Then remove quiet splash and add parameters as needs be.

Hope this helps.

---

### Post by Hajex on 2010-07-04
boot from usb flash instead of cd

---

### Post by sza on 2010-07-04
OK, I've tried what philinux told me to do and I managed to get into the LiveCD but the graphics is very low.

I am installing it now and hope that after I'll install the Nvidia driver it will work fine.

thanx a lot !!!

---

### Post by sza on 2010-07-04
OK, I've tried what philinux told me to do and I managed to get into the LiveCD but the graphics is very low.

I am installing it now and hope that after I'll install the Nvidia driver it will work fine.

thanx a lot !!!

---

