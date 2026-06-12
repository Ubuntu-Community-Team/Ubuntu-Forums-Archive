---
title: "Sound broken after installing Userful Multiplier"
date: 2010-06-27
forum: General Help
---

### Post by sumpm1 on 2010-06-27
Hey guys. I recently tried out Userful Multiplier on Ubuntu 9.10. It screwed up my audio badly and I uninstalled it.

Now my sound is broken. If I open alsamixer, I only get the following picture, and I can only adjust the card "Pulseaudio" as you can see in the picture. So I have lost adjustment of my inputs and outputs.

Now I am able to adjust my other inputs if I use the command alsamixer -c 0 where 0 is my default sound card. But the adjustments are not correct from this page.

Furthermore, I am finding that my sound in pulseadio is LOCKED to the current running application. So if I am running mplayer, and turn mplayer up, it turns my MASTER volume up! And also my sound has become quite quiet because of this.

What can I possibly do to correct this?

[img]http://img337.imageshack.us/img337/3986/screenshot1wr.png[/img]

---

### Post by Userful on 2010-07-14
* Laptops are generally not suited for the Userful Multiplier software, as it was designed for desktops.

* Currently the Ubuntu software repository does not contain the updated version of Userful Multiplier that is compatible with Ubuntu 9.10.  To download the latest version please click here: [http://www.userful.com/support/all-downloads/umx-download](http://www.userful.com/support/all-downloads/umx-download)

* We're not sure whether your uninstall was via Synaptic or command line but to fully uninstall our software and restore settings please use the following command:  
sudo apt-get remove userful-multiplier

If that is the method you used to uninstall, here are a few other options:

* 1 - Kill the Pulseaudio process, then uninstall Pulseaudio, reboot, and that may fix the problem

* 2 - For an alternate method of controlling sound, you could install PulseAudio Device Chooser from the Ubuntu Software Center.

For further assistance, please feel free to contact Userful's support team [http://support.userful.com/wiki/index.php/Contact_Userful](http://support.userful.com/wiki/index.php/Contact_Userful)

Userful Support Team

---

### Post by Twitch6000 on 2010-07-14
> **Userful said:**
> * Laptops are generally not suited for the Userful Multiplier software, as it was designed for desktops.

* Currently the Ubuntu software repository does not contain the updated version of Userful Multiplier that is compatible with Ubuntu 9.10.  To download the latest version please click here: [http://www.userful.com/support/all-downloads/umx-download](http://www.userful.com/support/all-downloads/umx-download)

* We're not sure whether your uninstall was via Synaptic or command line but to fully uninstall our software and restore settings please use the following command:  
sudo apt-get remove userful-multiplier

If that is the method you used to uninstall, here are a few other options:

* 1 - Kill the Pulseaudio process, then uninstall Pulseaudio, reboot, and that may fix the problem

* 2 - For an alternate method of controlling sound, you could install PulseAudio Device Chooser from the Ubuntu Software Center.

For further assistance, please feel free to contact Userful's support team [http://support.userful.com/wiki/index.php/Contact_Userful](http://support.userful.com/wiki/index.php/Contact_Userful)

Userful Support Team

If he removes pulseaudio it will try to uninstall alot of extra stuff like gnome-desktop.

Instead he should just go to system-preferences-sound. From there he can switch from pulseaudio to alsa or oss. I suggest oss.

---

