---
title: "grub boot issue"
date: 2011-04-08
forum: General Help
---

### Post by Glaucos60 on 2011-04-08
Hi all !

I don't know if it's the best place to post this, but i experienced a grub issue :P 
I installed ubuntu in windows XP from installation cd but i already had Debian in dual boot with windows, but trying to format my debian partition made me lose grub, i don't know how but when i boot my pc now i get a grub rescue console : /

It says  

Welcome to GRUB!

error: file not found
Entering rescue mode...
grub rescue>

i put my root in (hd0,4)
root=(hd0,4)

then

ls (hd0,4)/boot
./../ Sytem.map-2.6.26-2-686 config-2.6.26-2-686 vmlinuz-2.6.26-2-686 initrd.img-2.6.26-2-686

i don't know how to load the kernel since i seem to have no grub folder in that partition...
Can I find a way to boot from a ubuntu live CD or somethink like that from grub rescue ?
Since linux command does not work to load kernel, how can i load my kernel so i can install grub : D

Thanks in advance,

Glaucos

---

### Post by Dutch70 on 2011-04-08
If what you want to do is reinstall grub2, go here...
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Glaucos60 on 2011-04-09
Hi,

thanks for the response ! I couldn't boot from live CD since i can't select my cdrom drive in boot order but i did something similar with a grub rescue usb, so i could reinstall grub ([http://liveusb.info/dotclear/index.php?#googtrans/fr/en](http://liveusb.info/dotclear/index.php?#googtrans/fr/en)). :D

---

### Post by Dutch70 on 2011-04-09
So did you get it fixed?

---

### Post by Glaucos60 on 2011-04-09
Yes, the USB rescue could detect all OSes and i am now able to boot normally ; )

Thx for help !

---

### Post by Dutch70 on 2011-04-09
You're welcome. Glad to hear you got it going. :D

Please mark the thread "Solved" with "Thread Tools" at the top of the page, so others with you issue can find it & people won't keep trying to help you.

---

