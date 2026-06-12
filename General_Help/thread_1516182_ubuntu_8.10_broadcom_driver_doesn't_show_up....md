---
title: "ubuntu 8.10 broadcom driver doesn't show up..."
date: 2010-06-23
forum: General Help
---

### Post by Yep on 2010-06-23
Hey linux people! 

I installed Ubuntu 8.10 on my mom's HP pavillion DV6000 laptop, and I'm having problems getting the broadcom wireless card to work. I've done a few other machines with broadcom drivers with little to no problem, but this one is acting a fool. When I do the lspci in the terminal it doesn't list any network controllers at all...any help from here?

thanks 
Tim

---

### Post by snowpine on 2010-06-23
Hi Tim,

The Ubuntu Broadcom documentation is pretty good: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Keep in mind that Ubuntu 8.10 is obsolete and no longer supported, so you may have difficulty installing the necessary packages. I would recommend 10.04, the current release.

---

### Post by Yep on 2010-06-23
thanks for the fast response.

I read that tutorial and went through the process with no success, although everything installed "correctly" with no errors.

Even if the driver isn't installed the hardware should appear in the list of installed hardware right? This is where i'm getting stuck, as the broadcom unit is not appearing after the lspci command. i'm getting a buddy to bring a wireless PC card to slide in and hopefully get some connections going so I can update this thread while on that troubled machine.

---

### Post by snowpine on 2010-06-23
It could be something really simple, is there a keyboard combination (like Fn+F2 for example) that toggles the wifi on and off? Or what about rebooting and making sure the networking card is enabled in BIOS? Does wifi work using Windows (or a different Linux distro with built-in Broadcom support like Mint)?

---

### Post by Yep on 2010-06-24
tried Mint with the same results. The machine doesn't detect the network card. The switch on the front of the machine doesn't do anything. Any more ideas?

edit: been doing some research and have found that this HP pavilion series is having issues with the motherboard and its relation to the broadcom card...gonna call up HP and see what they can do for me. Probably nothing. 
Thanks for the help. i'll update later if i get any results...

---

