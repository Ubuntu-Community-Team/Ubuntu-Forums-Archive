---
title: "Nvidia Drivers Make Things Worse!"
date: 2009-10-29
forum: General Help
---

### Post by The Titan on 2009-10-29
I have been attempting to install the Nvidia drivers for my onboard GeForce 4 MX and I am having some serious issues.  

When I am not using the Nvidia drivers i am limited to 800x600 resolution.  This is really not going to be usable for me...
I use the "Hardware Manager" to install the drivers and I restart, after logging in i realize that now I am limited to 640x480 and 24 bit color! I then have to restart and go to the restore option in grub to restore the grub file.

I have never had this issue with any other version of linux (I am using 9.04).  But this is the  first time I have installed Ubuntu on this computer.

If anyone has any Idea what could be going on please help me out.  
Thank you,
Daniel

---

### Post by doppis on 2009-10-29
Are you using 32 or 64 bit? Which ever one...make sure your selecting the right driver.  I was having that problem too.

---

### Post by lovinglinux on 2009-10-29
I'm not sure about this, but as far as I know, the nvidia MX series is an old budget graphics card. So perhaps you will get better performance if you enable the oldest driver available in the Hardware Drivers tool, instead of installing the latest one.

According to nvidia download site, the correct driver for your card is 96 (96.43.13). Do you get that option on the Hardware Drivers tool?

---

### Post by The Titan on 2009-10-30
I just figured this out, 96 was the recommended one but I had to manually install the 71 because it is a geforce4 MX not just geforce MX.  I thing ubuntu got confused about all this or something.  Not really sure how all of that works =/

---

### Post by lovinglinux on 2009-10-30
> **The Titan said:**
> I just figured this out, 96 was the recommended one but I had to manually install the 71 because it is a geforce4 MX not just geforce MX.  I thing ubuntu got confused about all this or something.  Not really sure how all of that works =/

But the recommended driver for GeForce 4 MX is 96. Anyway, is it working good now?

---

