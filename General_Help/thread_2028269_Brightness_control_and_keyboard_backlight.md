---
title: "Brightness control and keyboard backlight"
date: 2012-07-17
forum: General Help
---

### Post by polymorphism on 2012-07-17
Hi,
I just installed ubuntu 12.04 and found out that neither the brightness control or keyboard backlight work on my Sony Vaio VPCF236FM.
 It has an nVidia Graphics Card. I think many people have the same problem. If anyone know how to fix it. 




Please help. Thank you.

---

### Post by adymitruk on 2012-07-18
Same problem with Asus g74sx. Tried a number of solutions. Keyboard backlight works, but screen brightness does not.

---

### Post by Toz on 2012-08-03
> **polymorphism said:**
> Hi,
I just installed ubuntu 12.04 and found out that neither the brightness control or keyboard backlight work on my Sony Vaio VPCF236FM.
 It has an nVidia Graphics Card. I think many people have the same problem. If anyone know how to fix it. 




Please help. Thank you.

Hello and welcome to the forums. 

Please have a look at the following PPA: [https://launchpad.net/~voria/+archive/ppa/]("https://launchpad.net/~voria/+archive/ppa/") for information and a solution to backlight on Sony laptops.

---

### Post by Toz on 2012-08-03
> **adymitruk said:**
> Same problem with Asus g74sx. Tried a number of solutions. Keyboard backlight works, but screen brightness does not.

@adymitruk, 
your issue is slightly different in that your notebook is an Asus. If your notebook has the nvidia card and you have installed the proprietary drivers, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of your /etc/xorg.conf file.

If, on the other hand, you don't have an nvidia card, try adding **acpi_backlight=vendor** to the kernel boot line. 

And as for controlling the keyboard backlight, have a look at this link: [http://hentenaar.com/serendipity/index.php?/archives/54-Controlling-the-Keyboard-Backlight-on-the-ASUS-G74SX.html]("http://hentenaar.com/serendipity/index.php?/archives/54-Controlling-the-Keyboard-Backlight-on-the-ASUS-G74SX.html").

---

### Post by messiah5150 on 2012-08-11
> **Toz said:**
> @adymitruk, 
your issue is slightly different in that your notebook is an Asus. If your notebook has the nvidia card and you have installed the proprietary drivers, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of your /etc/xorg.conf file.

If, on the other hand, you don't have an nvidia card, try adding **acpi_backlight=vendor** to the kernel boot line. 

And as for controlling the keyboard backlight, have a look at this link: [http://hentenaar.com/serendipity/index.php?/archives/54-Controlling-the-Keyboard-Backlight-on-the-ASUS-G74SX.html]("http://hentenaar.com/serendipity/index.php?/archives/54-Controlling-the-Keyboard-Backlight-on-the-ASUS-G74SX.html").

Hi, so I am also running a G74sx with an Nvidia card, and experiencing the same issue.  I tried to edit the "xorg.conf" file, but it does not exist in the /etc folder (opens a blank file as in create new). It does come up in a sub folder "X11" and I have seen a XORG.CONF Folder... I'm not so sure either is it.

Can you be a little more specific? I would like to try this fix to see if it works. 

Thanks

D

---

### Post by Toz on 2012-08-11
> **messiah5150 said:**
> Hi, so I am also running a G74sx with an Nvidia card, and experiencing the same issue.  I tried to edit the "xorg.conf" file, but it does not exist in the /etc folder (opens a blank file as in create new). It does come up in a sub folder "X11" and I have seen a XORG.CONF Folder... I'm not so sure either is it.

Can you be a little more specific? I would like to try this fix to see if it works. 

Thanks

D

The file is actually located at /etc/X11/xorg.conf and is only present if you're using the proprietary nvidia driver.

---

### Post by messiah5150 on 2012-08-12
> **Toz said:**
> The file is actually located at /etc/X11/xorg.conf and is only present if you're using the proprietary nvidia driver.

Excellent. 

Code added to the .conf file.  Screen brightness for Nvidia on Asus G74sx working fine. 

For me, this issue is solved, but not sure about polymorphism

Thank you for the help.

D

---

### Post by messiah5150 on 2013-01-27
Ok...so I have found another issue I think...or user error lol

I used the HDMI output to "CLONE" / "TWIN VIEW" to my TV. Basically using it as a monitor with the lid closed on my laptop.

When I use just the laptop and try to dim the screen brightness using the FN keys, I get indication that the brightness is either going up or down but nothing actually happens.

I tried placing the code in the xorg.conf file in the X11 folder again, but NVIDIA has a bunch of code in it.  So, I placed it at the beggining of the file and when I rebooted, I got stuck at the Plymouth screen (Purple screen, UBUNTU logo...5 red dots...hang).
Obviously I've done something wrong. I use an Ubuntu CD to boot up into demo mode and edit the file...bit of a pain.

Is there a way to get the best of both worlds here. Basically if I'm hooked into the TV..all is good.

If I go on the laptop and run on battery, I'd like to be able to dim the screen to conserve battery life.

Thanks!

D

---

