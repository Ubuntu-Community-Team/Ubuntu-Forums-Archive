---
title: "how to update drivers of windows xp (in virtuabl box) in ubuntu?"
date: 2010-02-03
forum: General Help
---

### Post by soomro on 2010-02-03
I am afraid is this is related topic :confused:

but I have istalled windows XP in my virtual box OSE in my linux, for trying to run an online game (it crash again and again with wine-doors) but the game gives error that I need to update my drivers to run that game...

I tried to install the my intel board and graphic drivers but the setup gives an error that it does not meet the minimum requirements, so how do I run the game??

---

### Post by Vignesh S on 2010-02-03
How much graphics memory did you allocate to the virtual machine? Also check how much RAM you allocated, and see if the error comes up again :)

---

### Post by NightwishFan on 2010-02-03
You need to install the Virtualbox guest editions. There is an Ubuntu package to do so.
[Install Guest Additions on Karmic]("apt://virtualbox-guest-additions")

You have to boot the virtual XP in safe mode, I think hold f8 right before it boots up splash screen to do so. Then mount virtualbox guest addition iso (its in /usr/share/virtualbox). Run the installer for Windows Guest Additions and reboot. Now you have 3d support.

I also recommend enabling Vt-x if you BIOS supports it. I am not sure how to check if it does.

Please ask if you need any help.

---

### Post by soomro on 2010-02-03
I have allocated 5gb hard disk, and 256Mb RAM

and I have already installed guest additions plus wine D3D.

I increased the RAM to 415 but still gives the same error :S
I have 1GB of over all RAM, when I give it 512Mb RAM, guest and host both Operating systems freeze.

and there is 2GB free space in the guest OS partition..

EDIT: my bad, grapbics memory was too low and 3d acceleration was disabled XD

but after I gave it 56Mb graphics memory (which is minimum required by the game)
it displays 800x600 reso only? what to do to fix it? the game screen is all cropped :S

---

