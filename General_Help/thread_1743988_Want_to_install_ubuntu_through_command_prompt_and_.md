---
title: "Want to install ubuntu through command prompt and from external hard disk."
date: 2011-04-29
forum: General Help
---

### Post by rj.24 on 2011-04-29
I want to install ubuntu from an external hard disk.

---

### Post by lisati on 2011-04-30
*Thread moved to **General Help**.*

---

### Post by lykwydchykyn on 2011-04-30
Can you be a little more specific?  What's your setup, and what limitations are you facing?

---

### Post by bcn17 on 2011-04-30
You could use Grub2. 

Instal Grub2 to a folder on a harddisk that is bootable by your bios. (Don't use a HD plugged into the 5th or 6th SATA port) 
EDIT: I Guess in your case install it to a folder on your external harddisk. Something like "/boot/". 

Then, put the ubuntu.iso on the same HD. Maybe in "/boot/iso/".

Then edit the /boot/grub/grub.cfg to look something like this except replace your isoimage in both places necessary. 

```
menuentry "Ubuntu Live 9.10 64bit" {
 loopback loop /boot/iso/ubuntu-9.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-desktop-amd64.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}
```

Once you boot into the live environment you are homefree. Select whatever HD you want to install it to. Athough, I'm not sure if you can install it to the same external drive. But maybe you can! 

This is where I got the above code. I used it successfully to install from a USB drive, which should be the same as an external. 
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

This is a very informative GRUB2 explanation. 

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

GL.

---

### Post by rj.24 on 2011-05-01
thank you friends for your help 

was successfully able to install ubuntu.


firstly was using a window7 But now wanted to use something different and want to go for ubuntu But was not able to burn a cd for ubuntu due to problem on a cd drive so was trying to ask whether there was some other way i.e. with the help of  external hard disk or pen drive i can format my windows.

---

### Post by rj.24 on 2011-05-01
Wireless  networks not working on ubuntu



Problem which is coming is device not found firmware not present.

what should i do to make that wireless connection work

---

### Post by lykwydchykyn on 2011-05-01
Check the "hardware drivers" tool to see if there are proprietary drivers needed.  If so you will need to plug in the wired connection in order to download them.

If that fails, post the output of the "lspci" command so that we know what wireless chipset you have.

---

### Post by rj.24 on 2011-05-06
How to post the output of the "Ispci" command





> **lykwydchykyn said:**
> Check the "hardware drivers" tool to see if there are proprietary drivers needed.  If so you will need to plug in the wired connection in order to download them.

If that fails, post the output of the "lspci" command so that we know what wireless chipset you have.

---

### Post by dozycat on 2011-05-06
I know you solved your problem but another option and maybe easier was to install ubuntu inside an usb memory. it is possible to create one from windows.

---

### Post by oldfred on 2011-05-06
It is lspci not Ispci. El and not capital, Often best to copy & paste into terminal, then copy results back to here.

```
lspci
```

---

