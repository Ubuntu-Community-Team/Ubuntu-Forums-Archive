---
title: "A stupid question about making an installation cd"
date: 2009-08-23
forum: General Help
---

### Post by Affrikka on 2009-08-23
Hey everyone!

I want to install ubuntu studio, and I searched up how to make the installation cd so that I can pop it in my computer and install it. The instructions say to put in a blank cd, which I did, and a window pops up that says to drag the files you want onto the cd and click burn. I did that, I put the ubuntu studio .iso file on there, as well as these weird .gpg files that were on the list of files on ubuntu studio's download page.

I click burn and it says there isn't enough room. I now realized that my blank cd is only 700mb, as is ALL of my blank cds, and ubuntu studio's .iso is 1.3gbs!

Is there something I'm doing wrong? Or should I just do it like I did before where you put it on a flash drive and install it from there?


Thanks!

Mathieu

---

### Post by P4man on 2009-08-23
You cant drag&drop an ISO file to cd. It has to be burned to cd with a program that understands the ISO image.

Here is how:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Affrikka on 2009-08-23
yeah, The CD is still too small, I right clicked the iso image and said burn to disc and it still gives me a message saying "please choose another disc, the files is too large even with the overburn function"

---

### Post by P4man on 2009-08-23
sorry, I didnt read carefully. didnt realize ubuntu studio iso is >1GB.
You'll need a DVD or usb stick to install it. Or you can install regular ubuntu first, then "upgrade" it to ubuntu studio.

---

### Post by Affrikka on 2009-08-23
okay thats what i thought i had to do.

thanks so much for your help though!

---

### Post by P4man on 2009-08-23
If you want to install from a USB stick, here is how:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you want to install normal ubuntu from a cd (only needs ~600Mb),  after installing it type in a terminal:

```
sudo apt-get install ubuntustudio-desktop
```

and it will be transformed in to a ubuntu studio install.

---

