---
title: "Adjusting Screen Brightness?"
date: 2011-12-02
forum: General Help
---

### Post by beidmann on 2011-12-02
My screen brightness is stuck on the maximum brightness and I can't seem to adjust it.  When I adjust it manually on the keyboard, the slider shows up as it does for volume changes and slides down but the brightness doesn't adjust. When I go into system settings, screen, and adjust it, it still doesn't change. 

Anyone have an idea how to rectify this?

---

### Post by beidmann on 2011-12-02
Can anyone help me with this?

---

### Post by Basher101 on 2011-12-02
it looks like you have the same problem as i had on my laptop, only in the opposite direction. I was stuck with NO brightness at all - meaning i got no backlight, but not a blackscreen. To fix it i did the following:

type in a terminal: ```
sudo gedit /etc/rc.local
``` and there you will see at the very most bottom a red colored [COLOR="Red"]EXIT[/COLOR]. Just above that "exit" type the command ```
setpci -s 00:02.0 F4.B=00
``` and save the settings. Next file you will have to edit is your Grub config file. Type into a terminal ```
sudo gedit /etc/default/grub
``` there you will see different settings. Now look for the line that looks like this: > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add "acpi_osi=Linux" at the end so that the line looks like this after editing:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Green"]acpi_osi=Linux[/COLOR]"

this should fix your problem. the only thing that got BROKEN is the indicator app that shows you that "bar" of the brighntess and that it is reversed (UP arrow increses brightness and DOWN decreses the brightness). But this is a price i gladly pay to change the brightness. 

If you do not want to make those "permanent" changes, you can also just adjust it by command with ```
sudo setpci -s 00:02.0 F4.B=[COLOR="Red"]XX[/COLOR]
``` where in XX you replace it with HEX code (reaching from 00 = 0 ([COLOR="Cyan"]brightest[/COLOR]) to FF = 255 ([COLOR="Navy"]darkest[/COLOR]))



regards.



p.s. you may have to update your grub with```
sudo update-grub
``` for the changes to take effect

---

