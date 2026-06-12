---
title: "Graphics Display Question"
date: 2011-10-11
forum: General Help
---

### Post by nerdyguy64 on 2011-10-11
I put ubuntu 11.04 on a portable hard drive to bring back and forth to my dad and moms house, my parents are divorced, and its easier to transport a little hard drive then my big computer. So im wondering, i have my graphics driver installed for my computer at my moms house installed on my ubuntu hard drive, but when i put it in my dads computer to use, i get the grub, and get the purple display and then it goes black, im thinking maybe the graphics for my dads computer isnt installed on my hard drive, is there a way that ubuntu can pick it up, and use the graphics display like on the cd, that works for all and then i could login and install the correct drivers. Anyone know?

---

### Post by Mark Phelps on 2011-10-11
IF the driver is one of the restricted ones (as in AMD or NVidia), I believe that you can not do what you want to do -- migrate the drive from one PC to another.  If you go back to your PC and replace the driver with an open-source driver, I believe that then, when youn connect the drive to the other PC, it will see the video card and automatically install the proper other open-source driver.  But with restricted drivers, it will not do this.

---

### Post by nerdyguy64 on 2011-10-11
> **Mark Phelps said:**
> IF the driver is one of the restricted ones (as in AMD or NVidia), I believe that you can not do what you want to do -- migrate the drive from one PC to another. If you go back to your PC and replace the driver with an open-source driver, I believe that then, when youn connect the drive to the other PC, it will see the video card and automatically install the proper other open-source driver. But with restricted drivers, it will not do this.
 
Okay, on my PC (which is installed on ubuntu) is Nvidia geforce 7600, on the other computer its a AMD Radeon HD 6350, is it possible to install both drivers on the computer, like to have both graphics drivers on the ubuntu hard drive. Hopefully i can do it....
 
-dan

---

### Post by Mark Phelps on 2011-10-11
I don't believe that you can install two sets of very different restricted video drivers.  I believe that the last one installed is the one that Ubuntu will attempt to use.

With open-source drivers, it is able to automatically install the driver it needs -- which is why folks can install to USB, remove that, plug it into another PC, boot from it, and then use it.

---

### Post by nerdyguy64 on 2011-10-12
> **Mark Phelps said:**
> I don't believe that you can install two sets of very different restricted video drivers.  I believe that the last one installed is the one that Ubuntu will attempt to use.

With open-source drivers, it is able to automatically install the driver it needs -- which is why folks can install to USB, remove that, plug it into another PC, boot from it, and then use it.

Im still a bit confused, like I know what it means "open-source" but how do i go about like installing it. Do i just install one driver that contains the ability to have both Nvidia and AMD in the driver? And where might that be found?

---

### Post by 23dornot23d on 2011-10-12
If its a Desktop Computer ..... then try to get the graphics card changed .....  one to match the other ...... ( Nvidia tends to be more widely used and set up for Linux to work easily ) 

I would have Nvidia in both ....

I have two systems and I do what you are proposing to do ...... 
one has a Nvidia 6300
the other Nvidia 9300

and I swap my USB drives from one to the other and they work ......

unless of course you can get it working with the previous suggestion
> 
With open-source drivers, it is able to automatically install the driver  it needs -- which is why folks can install to USB, remove that, plug it  into another PC, boot from it, and then use it.


Note - it would probably be simpler with both graphics cards being the same or similar ......

---

### Post by nerdyguy64 on 2011-10-12
> **23dornot23d said:**
> If its a Desktop Computer ..... then try to get the graphics card changed .....  one to match the other ...... ( Nvidia tends to be more widely used and set up for Linux to work easily ) 

I would have Nvidia in both ....

I have two systems and I do what you are proposing to do ...... 
one has a Nvidia 6300
the other Nvidia 9300

and I swap my USB drives from one to the other and they work ......

unless of course you can get it working with the previous suggestion

I dont think ill be able to change it... so are you saying that its not possible to have Nvidia and AMD on the system. Is there like a grapics that can be used on any and all systems, like the one of the live CD. Can i use that one? that one is multi graphics...

---

### Post by nerdyguy64 on 2011-10-12
Basically i just want to know if there is a universal graphics driver that works for all!

Like the one on the Live CD

---

### Post by Mark Phelps on 2011-10-12
> **nerdyguy64 said:**
> Basically i just want to know if there is a universal graphics driver that works for all!

Like the one on the Live CD

NO -- there is no universal driver.  The one on the LiveCD works because it doesn't actually install anything to your hard drive; instead, it creates a RAM disk in memory and installs there. When you reboot, RAM is cleared, and nothing remains on the PC.

You only have two choices that will work:
1) Have graphics cards in the PCs that are similar enough that the same driver will work for both
2) Remove restricted drivers from the Ubuntu install and go strictly with the open-source drivers.

---

### Post by CatKiller on 2011-10-12
Uninstall the proprietary driver. Then you'll be using the Free one(s) just like the live cd. That will play nice with any graphics card. The lack of cross-platform compatibility is one of the many flaws with proprietary software.

An sub-optimal alternative if you want to use both proprietary drivers is to boot into recovery mode from the GRUB menu each time you switch computers so that you can uninstall the proprietary driver from the command line and install the other proprietary driver & reboot.

---

### Post by nerdyguy64 on 2011-10-12
Okay, now where are those open source drivers found? At the official website? Or somewhere else? And sorry I'm a noob at Linux in general, my bad, and look at fourth post to see what the graphic cards I'm using. Thanks again

-Dan

---

### Post by nerdyguy64 on 2011-10-12
> **CatKiller said:**
> Uninstall the proprietary driver. Then you'll be using the Free one(s) just like the live cd. That will play nice with any graphics card. The lack of cross-platform compatibility is one of the many flaws with proprietary software.

An sub-optimal alternative if you want to use both proprietary drivers is to boot into recovery mode from the GRUB menu each time you switch computers so that you can uninstall the proprietary driver from the command line and install the other proprietary driver & reboot.

Thank you! That's what i wanted to hear, thanks agin, and to all that helped

---

### Post by RoyLongbottom on 2011-10-12
[FONT=Verdana][SIZE=2]I am currently working on benchmarks using USB drives to swap between PCs. My Ubuntu 11.04 has an nVidia driver installed. To run with other graphics, I have to boot to Recovery Mode and select Run In Fail Safe Graphics Mode. This works for normal displays but will not run OpenGL programs.[/SIZE][/FONT]
[SIZE=2][/SIZE] 
[SIZE=2]Roy[/SIZE]

---

### Post by nerdyguy64 on 2011-10-12
> **RoyLongbottom said:**
> [FONT=Verdana][SIZE=2]I am currently working on benchmarks using USB drives to swap between PCs. My Ubuntu 11.04 has an nVidia driver installed. To run with other graphics, I have to boot to Recovery Mode and select Run In Fail Safe Graphics Mode. This works for normal displays but will not run OpenGL programs.[/SIZE][/FONT]
[SIZE=2][/SIZE] 
[SIZE=2]Roy[/SIZE]

Yeah i wish that it was possible to have dual graphics drivers to be installed, like that the computer would boot up and chose the one that it needed, i guess something like that will be in time... hopefully, but thanks for that! :)

-Dan

---

### Post by CatKiller on 2011-10-12
> **nerdyguy64 said:**
> Yeah i wish that it was possible to have dual graphics drivers to be installed, like that the computer would boot up and chose the one that it needed, i guess something like that will be in time... hopefully, but thanks for that! :)

-Dan

That's exactly what the Free drivers do. The Free Nvidia driver is called nouveau, the Free Ati one radeon and the Intel one intel. When you boot up, the correct one is automatically picked. The proprietary ones aren't nearly as flexible, but they can perform better since we don't have access to their special sauce.

---

