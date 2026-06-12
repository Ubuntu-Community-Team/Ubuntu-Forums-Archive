---
title: "Ubuntu won't load after installing ATI Drivers"
date: 2011-08-21
forum: General Help
---

### Post by WikedX on 2011-08-21
The open source drivers don't work with HDTVs right so I needed to install ATI drivers

Im so upset because I FINALLY got Kernerl 3.0 working, but now recovery mode won't even work with the ATI drivers

I installed driver 11.8, my card is a 5770. Is there anything I can to do boot it up and somehow remove the bad drivers?

---

### Post by aeronutt on 2011-08-21
Does a grub menu appear?

If so, go the partition you want to boot, hit 'e', and add
radeon.modeset=0
to the end of the line that starts with:
linux /boot/vmlinuz....

then boot (key strokes to save edits and boot should be shown)

FYI, this edit is not persistent. Next time you boot, you'll need to do the same thing unless you fix your problem, or permanently edit your grub config file.

---

### Post by WikedX on 2011-08-21
Okay well I managed to get in and do apt-get purge fglxr or however the ATI drivers are spelled

Now evertything is hell and non of the compiz effects work, and I can't reinstall the ATI drivers. 

From the looks of it, I can move my files over to windows and just reinstall Ubuntu so I'm not too worried. But if anyone has another fix it would be great

---

### Post by WikedX on 2011-08-21
[LEFT]Okay so it seems Metacity runs fine

When I run sudo apt-get -f install it wants to reinstall the ATI drivers. I don't think that's such a hot idea

Also trying to install them from Ubuntu's restricted driver thing doesn't work.

I hate video drivers and anything to do with them, but I need the ATI ones on my desktop because I'm on an HDTV and I need them on my laptop for the sake of having battery life
[/LEFT]

---

### Post by aeronutt on 2011-08-21
About half way down, 'need to purge fglrx'.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

But, I have no idea if this is what your problem is.

---

### Post by WikedX on 2011-08-21
Well compiz works again after reading that, but trying to reinstall ATI's drivers from the Driver Manager is still giving me an error message >_< and I'm NOT about to try and use the .run file from their site again x_x

---

### Post by WikedX on 2011-08-21
Well again installing the ATI drivers stopped it from working and removing them got me back to compiz not working

So basically what I'm getting at is I should reinstall. I'll do it next week or something, but even if my display is unuseable at least I can use samba to stream files.

I'm thinking on my laptop once I compile a 3.0 kernel so I can get my thinkpad keys working, I might just skip out on the whole ATI driver thing. If I need battery life I can just boot into windows >_>

Thanks for the links though guys they at least got me back to a useable state. I won't mark as solved yet in case someone has a solution to have the drivers not break anything, but if there isn't anything by tomorrow I'll change it

---

### Post by Mark Phelps on 2011-08-22
I don't know your details ... but you DO know that the restricted drivers are kernel version specific, right?  

So, if you have a custom upgraded kernel, unless you grab the AMD drivers made for THAT kernel, any others you download and install won't work -- which appears to be the problem you're having.

---

