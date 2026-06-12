---
title: "New install problem"
date: 2011-02-25
forum: General Help
---

### Post by widiot on 2011-02-25
I have just started running ubuntu and  have ran into a couple of problems. I have been having a few  graphics problems with my card(not rendering openGL stuff and 3d stuff) so went for a new install. Everything goes fine  until the system reboots and then I just end up with a black screen with  my mouse cursor on it. To see  whats happening I Alt+Ctrl+F2 and the following screen comes up

[[IMG]http://img231.imageshack.us/img231/1015/dscf0006l.th.jpg[/IMG]]("http://img231.imageshack.us/i/dscf0006l.jpg/")

This just continues to count upwards displaying the same code afterwards.  My only option is to power down my PC and reboot,and at  the option screen I select the recovery mode. Then I need to select  the failsafe graphics mode and my ubuntu starts. In this failsafe mode my Pc has no problems rendering 3d stuff and openGL stuff. 

But seeing as this computer gets used by wife and kids and is alot of messing about to get it running this way I want to be able to just switch it on and let it boot up. So my fix for this is that I download and install  the ATI drivers from Administration>Additional drivers. This works! My PC now boots up and I have no need to intervene. However,this comes with the downside that I  am unable to run any 3d/openGL stuff. So what I am after is basically a way of uninstalling my ATI drivers and making my system boot up using the failsafe graphics settings. I dont want to enter  recovery mode/failsafe graphics every time I power up.I just want my system to  boot up  and work without having to change anything each and  every time

I am totally new to  all this so any  help is gratefully received

---

### Post by LinuxCharms on 2011-02-25
You must have had some patches on your computer that didn't act normally with the system.

Just re-install Ubuntu from a CD or a USB drive and you should be fine. :)

---

### Post by widiot on 2011-02-25
Thanks,but I have now installed 3 times in past 24 hours,and every time I end up with the same thing. The install is onto a clean partition on a system running XP on a seperate partition. I am not really sure what patches you are referring to as all I install is on the official ubuntu CD,and then I run  update manager. Is it likely that something that is selected in update manager is causing the problem? I just assumed(probably wrongly) that I should always download the latest builds when  prompted?

---

### Post by widiot on 2011-02-25
Further to the above problems I am unable to get  visualisations working when using media players. They show,but they dont  animate,and they cause my system to freeze. It seems as if any graphics intensive task is just killing my system. I just want to be able to run using  failsafe settings,and not using  the ATi driver,but as it says in OP I cant boot normally without the ATI drivers

---

### Post by widiot on 2011-02-26
Just bumping this to see if anyone can help.

---

### Post by kiyop on 2011-02-26
What version of Ubuntu are you using? 10.10?

At booting, press Shift key to display GRUB(1.98?) screen and type E key to modify the boot option.
Add 
xforcevesa
to the end of the line begining with "linux".
Type "CTRL" and "X" at the same time to boot.

If it works, 
"Application"-> "Accessory" -> "Terminal"
and enter
```
gksu gedit /etc/default/grub
```and type password, if the password is asked.

Gedit(text editor) will open.
Edit the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa"

Save and close gedit.

Then in the terminal,
```
sudo update-grub
```to apply the change.

Another candidate to add is:
nomodeset
i915.modeset=0
i915.modeset=1
It may depend on the graphics chipset.

If your /etc/X11/xorg.conf has special settings, it may cause the problem.

---

