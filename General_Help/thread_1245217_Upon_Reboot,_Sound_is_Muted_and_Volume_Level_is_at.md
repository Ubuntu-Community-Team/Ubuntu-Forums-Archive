---
title: "Upon Reboot, Sound is Muted and Volume Level is at Low"
date: 2009-08-20
forum: General Help
---

### Post by Buschbarber on 2009-08-20
Whenever I Reboot Ubuntu, the Volume icon in the System Tray is Muted and the Volume Level is set to Low. I Uncheck Mute and move the Volume Slider to 3/4. Everything is fine until Reboot.

---

### Post by Buschbarber on 2009-08-25
After trying many suggestions received from the Ultimate Fourm, I finally found a solution.

Any comments regarding the negative effects of using this procedure?


Re: Upon Reboot, Sound is Muted and Volume Level is at Low

Postby Moebius on August 23rd, 2009, 7:17 am
Hey Buschbarber,
Here's a possible workaround for you. The premise here is to set your volume to a comfortable level, save the settings, and then restore them at every reboot. Instructions as follows:

1.) Manually adjust the mixer settings to something that is a good default for your audio needs. These settings will be loaded every time you restart your computer.

2.) Change the file permissions for /var/lib/alsa/asound.state to enable read/write access for the group/others (open the folder in Thunar, then right-click the file, select properties, and go to the Permissions tab). If you don't do this, then the next step will give you a permission denied error.

3.) Open up a terminal and enter the command "alsactl store" (without the quotes). This stores your mixer settings in /var/lib/alsa/asound.state for later use.

4.) From The System / Preferences menu, go to Sessions and click the Add button.

5.) Enter the command "alsactl restore" (without the quotes) and the name and description of your choice. This causes the "alsactl restore" command to automatically run when you start your computer. The command restores you mixer settings from /var/lib/alsa/asound.state where you saved them earlier.

Hope this helps. (Thanks to [https://answers.launchpad.net/ubuntu/+question/68564](https://answers.launchpad.net/ubuntu/+question/68564) )

---

