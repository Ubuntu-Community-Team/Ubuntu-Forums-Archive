---
title: "Enable Desktop Effects?"
date: 2009-11-15
forum: General Help
---

### Post by Tramx on 2009-11-15
Well, I decided to give Debian a try. I'm having problems with enabling desktop effects similar to that of Ubuntu. I configured my graphics card, installed compiz and compiz-fusion but there is still no sign of any effects whatsoever. What else do I need? :confused:

---

### Post by MaxIBoy on 2009-11-15
What graphics hardware do you have?

For ATI: [http://wiki.cchtml.com/index.php/Debian](http://wiki.cchtml.com/index.php/Debian) (kind out of date, the latest drivers are 9.10, but those directions should still suffice.)

For nVidia: Not sure what the best tutorial is, I've never personally tried any of them.

For Intel: Should be working out of the box.

---

### Post by Tramx on 2009-11-15
I have NVIDIA Geforce GO 7400 and I am running Intel. But I don't seem to see the Desktop Effects tab in Appearance Preferences.

---

### Post by MaxIBoy on 2009-11-15
OK, so your graphics hardware is nVidia. Well, the download page for the right driver is on nVidia's website.
32 bit: [http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)
64 bit: [http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html)


I don't know how to set this up, having never owned an nVidia card. Google "Linux nVidia 190.42 driver installation" or something like that, plenty of tutorials should turn up... or you can wait around for someone to reply who owns an nVidia card...

---

### Post by Tramx on 2009-11-15
I have double checked that I had this exact driver already installed and running, however there is still the problem. :(

---

### Post by nikgare on 2009-11-15
Are you sure it's running?
Does it show up in hardware drivers?
Does it appear in the xorg logs?

---

### Post by Tramx on 2009-11-15
This is another problem, I don't have "Hardware Drivers" configuration installed under System. Please show me how to. Also how do you determine if it's running in xorg.

---

### Post by 23dornot23d on 2009-11-15
Goto the top Bar .... and choose ..........

System - Preferences - Display

do you get a screen like or similar to this ..... one .....



System - Administration - Hardware Drives .....

Also in this same menu should be the NVIDA- x Server Settings ...... if its installed properly .....

---

### Post by J-Buntu on 2009-11-15
> **tramx said:**
> this is another problem, i don't have "hardware drivers" configuration installed under system. Please show me how to. Also how do you determine if it's running in xorg.
________________________

--------deleted---------

---

### Post by Tramx on 2009-11-15
Yes I do, under System -> Nvidia X Server Settings. Also, it's weird my system does NOT have "Hardware Drivers" config. I will show you

---

### Post by 23dornot23d on 2009-11-15
Ok is all the information correct there for your graphics card ....


if so .....


goto

System  Preferences - Compiz config Settings Manager

and tick the box's for what you want

---

### Post by Tramx on 2009-11-15
Still doen't work...

---

### Post by 23dornot23d on 2009-11-15
> **Tramx said:**
> Yes and ok.


Yes and ok you have the compiz screen  ..... ?

if so have you tried any of the effects ....

Wobbly windows or something like thta to start with

some of the others need keys holding down to get them to work
and I rarely use the effects now .....


Can you do a screenshot of the Nvidia Display Settings ....  
similar to the one I did earlier ......

---

### Post by Tramx on 2009-11-15
Take a look. I selected Wobbly Windows but it doesn't wobble. I don't understand, I've done it before in Ubuntu, why not Debian?

Edit*

Ok I will.

---

### Post by Tramx on 2009-11-15
Here...

---

### Post by 23dornot23d on 2009-11-15
Ok the Driver appears to be fine .... ty

_____________________________________

Just check you have everything loaded up for compiz .....

in Synaptic .......

Mine looks like this .... hope this is all .... might just be something missing from Compiz

---

### Post by Tramx on 2009-11-15
Ok I seached Synaptic, here are my results.

---

### Post by 23dornot23d on 2009-11-15
Have you tried to get tha latest updates and re-install the packages ...

With it being Debian .... 

I am not sure if what you have are the latest ...... packages or not ....

This is as far as I can go with this ......

as from what I can see it looks to be ok ......

and should work ..... !!! ..


Have you seen this thread .... [http://ubuntuforums.org/showthread.php?t=659102](http://ubuntuforums.org/showthread.php?t=659102)

There is a Compiz Check Tool as well have you tried to run that ...

sudo wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check
sudo chmod +x compiz-check
./compiz-check


The output should look like this ...........

---

### Post by Tramx on 2009-11-15
Well, I did both but I guess Debian is just being stubborn. I don't know what else to do...

```
user@debian-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Debian GNU/Linux (5.0)
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [GeForce Go 7400] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by 3rdalbum on 2009-11-15
So... you've got Compiz and you've got 3D drivers.

All you need to do is run Compiz:

```
compiz --replace
```

P.S. There is no Hardware Drivers program and no Visual Effects tab in Appearance, in Debian. Those are two things that Ubuntu provides.

---

### Post by Tramx on 2009-11-15
OMG!!! It works! Thank you ALL very much!:p Now I can move on installing other packages. =D>

But wait, do I have to enter terminal everytime I turn it on? Can't I just have it running on start up?

Also, when I exit terminal the display all turns odd.

Edit*

(Solved) Go to System -> Preferences -> Sessions

Add -> compiz --replace -> OK

---

