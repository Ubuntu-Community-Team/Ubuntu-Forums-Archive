---
title: "Ubuntu 10.04 xorg.conf problems"
date: 2011-01-07
forum: General Help
---

### Post by framiss on 2011-01-07
In the progress of configuring a second monitor i got stuck on xorg.conf.

I have been following some guides avalible to setup the tweaks.

[http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/](http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/)

Im using Ubuntu 10.04.

I alwas get stuck on generating a new xorg.conf.
I've tried every possible way to get one but none is working.

I tried booting in reset mode
```
sudo X -configure
```and i got "SEGSEV in nill" segmentation fault

I read somewhere that the newer releases of ubuntu or X doesn't generate xorg.conf
instead sets up automatically.
So i got out one of the older cds that i have and booted a live session from cd

```
cd /etc/X11/
```and took the xorg.conf file and saved it on a usb stick
then booted up the new OS again and edited the file.

Question is really.

Do i need to have the complete .conf file or can i just create a new file and
edit it with the contents needed?

Does the computer boot like it used to without the xorg.conf setting up  the hardware automatically and then reads the tweaks in the .conf file  or will it only read the .conf file?

Can i use the xorg.conf file from an older version like i did when i  took it from the live cd boot session and just edit the file? Its from  the same computer.

---

