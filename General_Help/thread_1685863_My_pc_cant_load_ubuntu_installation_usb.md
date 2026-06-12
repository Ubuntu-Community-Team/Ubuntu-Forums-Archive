---
title: "My pc cant load ubuntu installation usb"
date: 2011-02-11
forum: General Help
---

### Post by manclip on 2011-02-11
Hello. I installed kubuntu 10.10 on my pc. But i didnt like it very much so i want to go back to Ubuntu, so i made a usb to install ubutnu again but when i connect it to my pc and make my pc booting from my usb comes that ubuntu image with the dots and i waited for an hour and it didnt load. So i made the usb again i didnt load again. So i thought of trying my old windows xp cd to see if windows loads but it didnt load the windows cd too. After that i went to the bios and i loaded the default configuration and try the cd and usb again but it is still not working. Can you help me please?   

thats the image with dots that i mean:[IMG]http://attachments.techguy.org/attachments/177098d1281923896/ubuntu_lucid_lynx_1.jpg[/IMG]

---

### Post by C.S.Cameron on 2011-02-11
You should be able to load and use Ubuntu Desktop from synaptic with your existing Kubuntu install.

---

### Post by manclip on 2011-02-12
> **C.S.Cameron said:**
> You should be able to load and use Ubuntu Desktop from synaptic with your existing Kubuntu install.
But i wanted to format my hdd. Do you think if i update my bios then i could install it from the usb?

---

### Post by williamts99 on 2011-02-12
Have you booted from USB on this computer before, or did you install from a disk?  Some computers can not boot from USB, please check the documentation from the computer manufacturer.

---

### Post by manclip on 2011-02-12
> **williamts99 said:**
> Have you booted from USB on this computer before, or did you install from a disk?  Some computers can not boot from USB, please check the documentation from the computer manufacturer.
think my computer can boot fom a usb, because i installed kubuntu from a usb.

---

### Post by williamts99 on 2011-02-12
That solves that issue, you will not need a BIOS update.  Please have a look at the user manual for your computer/motherboard, you will have to set the boot options so that it will boot from USB.  Then you just have to install Ubuntu the same way you installed Kubuntu.

---

### Post by Spyderkid on 2011-02-12
have a look at all of your bios prefrences also have a try at a ubuntu DVD?...

Also soon as you get onto that screen could you press F5 or any F key and tell us what it says.

---

### Post by manclip on 2011-02-12
> **williamts99 said:**
> That solves that issue, you will not need a BIOS update.  Please have a look at the user manual for your computer/motherboard, you will have to set the boot options so that it will boot from USB.  Then you just have to install Ubuntu the same way you installed Kubuntu.
The problem is that when i boot to the usb it keeps loading (shows that image that i show on my first post) and i waited 1 hour and nothing happened was still showing that image

---

### Post by manclip on 2011-02-12
> **Spyderkid said:**
> have a look at all of your bios prefrences also have a try at a ubuntu DVD?...

Also soon as you get onto that screen could you press F5 or any F key and tell us what it says.
I pressed f5 at athat screen and thi is what it says:

(process:275):gLib-WARNING**:getpwiuid_rc():failed due to unknow userid(0)
                                                                                                    stdin:error 0

---

### Post by williamts99 on 2011-02-12
> **manclip said:**
> I pressed f5 at athat screen and thi is what it says:

(process:275):gLib-WARNING**:getpwiuid_rc():failed due to unknow userid(0)
                                                                                                    stdin:error 0


Make sure to disable the floppy drive in the BIOS, this will usually revert to being enabled.  Then try again :)

What version of Ubuntu are you trying to install?  32bit or 64bit?  If you are trying an earlier version, please try 32bit 10.10 and maybe unplug your CD-rom drives for the installation.  Failing that, I would try a different USB memory stick.

Seems that for some, this is just an annoyance, and it still boots anyway, others are not as lucky.

---

### Post by manclip on 2011-02-13
> **williamts99 said:**
> Make sure to disable the floppy drive in the BIOS, this will usually revert to being enabled.  Then try again :)

What version of Ubuntu are you trying to install?  32bit or 64bit?  If you are trying an earlier version, please try 32bit 10.10 and maybe unplug your CD-rom drives for the installation.  Failing that, I would try a different USB memory stick.

Seems that for some, this is just an annoyance, and it still boots anyway, others are not as lucky.
Iam trying to install the 10.10 32 bit ubuntu. I will try disable the floppy.

---

### Post by manclip on 2011-02-13
> **williamts99 said:**
> Make sure to disable the floppy drive in the BIOS, this will usually revert to being enabled.  Then try again :)

What version of Ubuntu are you trying to install?  32bit or 64bit?  If you are trying an earlier version, please try 32bit 10.10 and maybe unplug your CD-rom drives for the installation.  Failing that, I would try a different USB memory stick.

Seems that for some, this is just an annoyance, and it still boots anyway, others are not as lucky.
I tried all of that and it didnt work , but then i burn a ubuntu cd and with the cd it worked. Thanks to everyone who helped me.

---

### Post by grahammechanical on 2011-02-13
I am glad that you got the Ubuntu install that you wanted. Have you identified what you did wrong? The screen that you saw is the same screen that we see when Ubuntu loads. We all see that screen. So, you must have created a Ubuntu installation that loaded from the USB drive and for some reason was faulty. You did not create a Live USB installation that would allow you to install Ubuntu on to the hard disc.

When you burn the Live CD download to disc you get a Ubuntu installation that loads from the CD and allows you to install from the CD. From the start you get a different screen to the one you saw. You get a screen that allows you choose to run Ubuntu or install Ubuntu. Is this not true? You do not see the screen that you saw until either Ubuntu has almost loaded or the installation process has been complete and the machine has rebooted.

Was the USB stick large enough to hold the Ubuntu Installation?

Regards.

---

### Post by manclip on 2011-02-13
> **grahammechanical said:**
> I am glad that you got the Ubuntu install that you wanted. Have you identified what you did wrong? The screen that you saw is the same screen that we see when Ubuntu loads. We all see that screen. So, you must have created a Ubuntu installation that loaded from the USB drive and for some reason was faulty. You did not create a Live USB installation that would allow you to install Ubuntu on to the hard disc.

When you burn the Live CD download to disc you get a Ubuntu installation that loads from the CD and allows you to install from the CD. From the start you get a different screen to the one you saw. You get a screen that allows you choose to run Ubuntu or install Ubuntu. Is this not true? You do not see the screen that you saw until either Ubuntu has almost loaded or the installation process has been complete and the machine has rebooted.

Was the USB stick large enough to hold the Ubuntu Installation?

Regards.
Actually first comes the screen with dots and then comen the window were you choose test or install ubuntu. And the usb stick was a 4gb more than enough for the live cd, and something strange is that i used that same usb stick to install ubuntu in another pc and it worked!

---

### Post by Spyderkid on 2011-02-14
This happened to me with Cd's and DVD's with the Glib warning*** thing.

the solution to this problem is to switch to the other media in my case USB i'm not sure why it happened but it works.


Its not the problem with the USB its not hard drive, im not sure why but i've narrowed it down to the hard drive because my computer need the motherboard replacing and I replaced all components appart from the Hard drive. I re-installed and that still happened untill I used the USB :)

---

