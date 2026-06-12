---
title: "Dapper installation - Nvidia error"
date: 2006-05-05
forum: General Help
---

### Post by ElderLars on 2006-05-05
i run Brezy and have updated to Dapper. But when i starting dapper after install it gives me error about my drivers. It cant start X windows decouse i dont have the drivers it says. I installed the drivers in Brezy... i use Nvidia FX5600
Do you have any ideas? Thank you

---

### Post by louis_nichols on 2006-05-05
Did you try installing the drivers in Dapper, then? You can do it from the command line.

When you get that error saying it can't start X, press Ctrl+Alt+F1 and it will take you to a command line terminal. Login there wih your user name an passwd and then issue the command

```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`

```
The password it will ask for after this is your user password. Then  give it time to install and reboot your computer to try logging in again.

Good luck!

---

### Post by ElderLars on 2006-05-06
i tried and it says that it is a conflict between nvidia-glx and nvidia-settings but 1.0-3ubuntu7 can fix it. how do i get that.

---

### Post by louis_nichols on 2006-05-06
Oh, that's strange. Then delete nvidia-settings from the command I posted. It's not that useful, actually. The drivers work without, it's just a GUI for certain configurations. I've never used it. I didn't install it either, the last time.

---

### Post by tseliot on 2006-05-06
[QUOTE=ElderLars]i tried and it says that it is a conflict between nvidia-glx and nvidia-settings but 1.0-3ubuntu7 can fix it. how do i get that.[/QUOTE]
In Dapper nvidia-settings is already included in nvidia-glx therefore the 2 packages conflict.

In other words, don't install nvidia-settings.

---

### Post by ElderLars on 2006-05-07
OK. But i did update from Brezy and the error ocured after the reboot. didnt it erase the old driver then? Or can i uninstall drivers, is there a uninstall command?

The first time i rebooted it came up a blue screen with text like this:

faild to load:  /usr/lib/xorg/modules/extensions/libGLcore.so
faild to load: "GLcore" (loader faild,7)
--"--         : "nvidia"(module does not exist,0)
                : no drives available

the above its not an exatcly copy of the text though....

---

### Post by tseliot on 2006-05-07
[QUOTE=ElderLars]OK. But i did update from Brezy and the error ocured after the reboot. didnt it erase the old driver then? Or can i uninstall drivers, is there a uninstall command?

The first time i rebooted it came up a blue screen with text like this:

faild to load:  /usr/lib/xorg/modules/extensions/libGLcore.so
faild to load: "GLcore" (loader faild,7)
--"--         : "nvidia"(module does not exist,0)
                : no drives available

the above its not an exatcly copy of the text though....[/QUOTE]
Try this:
sudo /etc/init.d/gdm stop (or kdm stop, if you use KDM)
sudo nano /etc/X11/xorg.conf

set the driver to "vesa" in the Section Device.

CTRL+O to save
CTRL+X to exit

then type:
sudo /etc/init.d/gdm start (or kdm start, if you use KDM)

Then follow my guide or use my script:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by ElderLars on 2006-05-08
Thank you! Now i can enter Gnome again. I will install the new Nvidia drivers as fast as i can reach internet again. I have some problems right now. Its not fun becous i want it to work. But on the other hand i installed Ubuntu to learn about Linux and Ubuntu.
I hope i can be to some help in the future!

---

