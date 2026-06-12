---
title: "Disable Unity and enable desktop effects in 11.04"
date: 2011-05-09
forum: General Help
---

### Post by Inopia on 2011-05-09
I upgraded to 11.04 when it was released and used Unity for a while. I wasn't really impressed with it and am planning to wait out for the next release until I test it again.

I switched over to ubuntu-classic session and everything seems to work as it used to - except for desktop effects. In older Ubuntus I could enable and disable them as needed under System->Appearance->Desktop Effects. There is no such menu anymore.

Do I have to downgrade to 10.10 or 10.04 to get Desktop Effects/Compiz support for classic Ubuntu? Is there some package I can install to get this working?

---

### Post by CoolJohnB on 2011-05-09
Try installing compiz manager, all the desktops effects work well in 11.04

---

### Post by Frogs Hair on 2011-05-09
If you want that option you may have to reinstall 10.10 or 10.04 . I think it is an all or none option , If you have a proprietary driver installed effects are activated and controlled with Compiz in Classic Gnome.

Check for other threads , because another user was inquiring about the same thing and that thread was unresolved . There may be a way to install the required packages to get the old settings back.

---

### Post by mcduck on 2011-05-09
> **Inopia said:**
> I upgraded to 11.04 when it was released and used Unity for a while. I wasn't really impressed with it and am planning to wait out for the next release until I test it again.

I switched over to ubuntu-classic session and everything seems to work as it used to - except for desktop effects. In older Ubuntus I could enable and disable them as needed under System->Appearance->Desktop Effects. There is no such menu anymore.

Do I have to downgrade to 10.10 or 10.04 to get Desktop Effects/Compiz support for classic Ubuntu? Is there some package I can install to get this working?

Just run "compiz --replace to start Compiz. You might want to disable the Ubnity plugin, though.

To make the change permanent you can either edit the window manager key in gconf-editor (desktop/gnome/session/required_components/windowmanager)  or add "compiz --replace" to your startup applications.

(The Effects tab in Appearance menu was removed because Unity runs on top of Compiz, so selecting the "none" option from that tab would have killed the whole desktop.)

---

### Post by Inopia on 2011-05-09
> **CoolJohnB said:**
> Try installing compiz manager, all the desktops effects work well in 11.04

I have CompizConfig Settings Manager installed but cannot find any dialog that allows enabling Desktop Effects.


> **Frogs Hair said:**
> If you want that option you may have to reinstall 10.10 or 10.04 . I think it is an all or none option , If you have a proprietary driver installed effects are activated and controlled with Compiz in Classic Gnome.

Check for other threads , because another user was inquiring about the same thing and that thread was unresolved . There may be a way to install the required packages to get the old settings back.

I use intel drivers and they are working with 3D applications as expected. I've had no problem with intel drivers in previous releases.

I've tried to search for an answer but have found nothing helpful. That is why I posted a new thread. It seems that if I want to use the old user interface I need to install an old release. :(

---

### Post by Inopia on 2011-05-09
> **mcduck said:**
> Just run "compiz --relace to start Compiz. You might want to disable the Ubnity plugin, though.

To make the change permanent you can either edit the window manager key in gconf-editor (desktop/gnome/session/required_components/windowmanager)  or add "compiz --replace" to your startup applications.

(The Effects tab in Appearance menu was removed because Unity runs on top of Compiz, so selecting the "none" option from that tab would have killed the whole desktop.)

Thanks this fixes everything :)

---

### Post by CJS99 on 2011-05-16
> **CoolJohnB said:**
> Try installing compiz manager, all the desktops effects work well in 11.04
May I please have a link?

Thanks!

---

### Post by CJS99 on 2011-05-16
When I use Ubuntu 11.04, My desktop gets all weird. I have a decent graphic card and I have had no problems with it in the past. Any ideas

---

### Post by K-Spaz on 2011-05-17
Today, I'm trying Ubuntu 11.04 for the second time now.  This time going to the classic desktop and attempting to get a working system back.  Are you seriously telling me they have done away with the "Settings" part of the menu, and that I need to google all this to go install it separately?  I hate to say it but as a user since 7.10 or so, this is the last straw.  No control center, no settings menu, no desktop effects config dialogs.  

If I'd wanted a crippled cell phone interface, I'd have bought an ipad.  This is like making turn signals in a car, optional.

---

### Post by mcduck on 2011-05-17
> **K-Spaz said:**
> Today, I'm trying Ubuntu 11.04 for the second time now.  This time going to the classic desktop and attempting to get a working system back.  Are you seriously telling me they have done away with the "Settings" part of the menu, and that I need to google all this to go install it separately?  I hate to say it but as a user since 7.10 or so, this is the last straw.  No control center, no settings menu, no desktop effects config dialogs.  

If I'd wanted a crippled cell phone interface, I'd have bought an ipad.  This is like making turn signals in a car, optional.

Control Center is there by default. Just look under the menu in the top right corner.

Settings menu is indeed removed, simply because Ubuntu is using Control Center instead (and the menu bar applet wouldn't even work with anything else than gnome-panel)

Desktop effects tab was removed from the Appearance dialog simply because if it was there, and somebody would change the setting to "none", that would break the desktop (as "none" would switch the window manager to Metacity, while Unity itself is a Compiz plugin and thus requires the desktop effects to be enabled).

In other words all the things you want are there. You don't need to install anything, just take a look around before jumping to conclusions. :D

---

### Post by Xander {MP} on 2011-06-01
How do you disable unity and get back to classic gnome? Is it all in the gconf file?

---

### Post by mcduck on 2011-06-01
> **Xander {MP} said:**
> How do you disable unity and get back to classic gnome? Is it all in the gconf file?

No, it's an option in the login screen. Just choose "Ubuntu Classic" from the Session dropdown near the bottom of the screen after selecting an user (but before typing in the password).

---

### Post by ad libitum on 2011-06-05
Hi, I'm also trying to enable desktop effects in 11.04. I see 2 solutions offered in this thread:

> **CoolJohnB said:**
> Try installing compiz manager, all the desktops effects work well in 11.04

> **mcduck said:**
> Just run "compiz --replace to start Compiz. You might want to disable the Ubnity plugin, though.

To make the change permanent you can either edit the window manager key  in gconf-editor  (desktop/gnome/session/required_components/windowmanager)  or add  "compiz --replace" to your startup applications.

I have installed compiz manager, along with fusion icon and emerald. I also have updated my video drivers, which were able to use desktop effects no problem in 10.10. I have used the compiz --replace command but it didn't seem to have an affect.

Can someone who has managed to get desktop effects (and maybe emerald) to work in 11.04 tell us how you've done it? Is it possible to log in with Unity, and then disable Unity and achieve desktop effects this way? Or, is there a surefire way of continuing to use "Ubuntu Classic" but still having desktop effects?

---

### Post by mcduck on 2011-06-06
> **ad libitum said:**
> Hi, I'm also trying to enable desktop effects in 11.04. I see 2 solutions offered in this thread:





I have installed compiz manager, along with fusion icon and emerald. I also have updated my video drivers, which were able to use desktop effects no problem in 10.10. I have used the compiz --replace command but it didn't seem to have an affect.

Can someone who has managed to get desktop effects (and maybe emerald) to work in 11.04 tell us how you've done it? Is it possible to log in with Unity, and then disable Unity and achieve desktop effects this way? Or, is there a surefire way of continuing to use "Ubuntu Classic" but still having desktop effects?

Compiz is enabled by default if you use Unity or the Ubuntu Classic sessions. Only the "Ubuntu Classic (No Effects)"-option runs without Compiz.

(Don't try disabling the Unity plugin while running the Unity session, you'd just end with anon-functional desktop without any panels or menus.)

I've understood that getting Emerald to work would need some tricks, but as I'm not using it myself I can't say much about that. (I can't really see why it would require any special tricks, though, at least if you are using the Classic desktop).

---

### Post by muscule_boy on 2011-09-08
To enable desktop effects in **Ubuntu 11.04** when not using Unity, you have to configure desktop using the **CompizConfig Settings Manager** (You will have to make sure that you have the settings manager installed using the Synaptic Package Manager by searching for "compizconfig"). Once this installed and the compiz configuration window open, go the effects category and then select the effects you want. I selected Animation, Water Effect, Window Decoration (must have this) and Wobbly Windows. You can also click on the Desktop category and add more such as the "Viewport Switcher", "Desktop Cube" and "Rotate Cube". You may get some other dialogs if some features require other things to be enabled or disabled.

Good luck.

---

