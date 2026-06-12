---
title: "Why does SKype automatically start ?"
date: 2009-11-16
forum: General Help
---

### Post by laurent255 on 2009-11-16
Hi

i've spent some time trying to understand that ... but still no answer :-(

I would like to be able to launch Skype manually, when i need it;  but it always auto launchs on Gnome session startup.


I've removed any entry in Gnome startup application manager
I've not found any option in Skype itself stating i want it to launch on startup
i've been through some /usr/share/gnome/autostart/ or ~/.config/autostart folders

Any idea please ?

(on Ubuntu 9.10 32 bis)

---

### Post by Bruce H on 2009-11-17
This isn't really an answer, but you can prevent skype from signing in automatically when it starts. Look in the skype options. At least then you won't be announcing to the world that you've logged in every time.

---

### Post by laurent255 on 2009-11-17
thanks, that's what 'm actually doing.

---

### Post by anonSam on 2009-11-24
You could try installing BootUp-Manager in SPM or the software center and maybe it would be listed there. On my system "Startup Applications" and "Boot-up-Manager" display different entries.

---

### Post by lisati on 2009-11-24
Another option is to shut down skype manually before powering down your computer, so when you next log in, skype isn't remembered as part of your session.

---

### Post by danrche on 2009-11-25
> **lisati said:**
> Another option is to shut down skype manually before powering down your computer, so when you next log in, skype isn't remembered as part of your session.





You can always delete the skype instance in the start up applications, that'll keep it from starting, also uncheck the box in the options tab that says "Automaticly remember running applications when logging out".

---

### Post by laurent255 on 2009-11-25
thanks danrche, but still, skype starts on gnome session startup !

---

### Post by anonSam on 2009-11-25
Try this command to remove any Skype start-up entries:

```
sudo update-rc.d -f skype remove
```

---

### Post by laurent255 on 2009-11-27
still not !

i've done :
* sudo update-rc.d -f skype remove
* sudo reboot
=>skype still starts !

then :
 * sudo apt-get remove --purge skype
 * sudo reboot
=> at last! skype did not auto start

i then reinstalled skype, and it starts again automatically ....

---

### Post by blueridgedog on 2009-11-27
Can you post the output of the following, just so we can see what is starting automatically?

```
ls /home/USER/.config/autostart
```

and 

```
ls /etc/xdg/autostart
```

Change USER to match your user account.

---

### Post by scorp123 on 2009-11-27
> **anonSam said:**
> Try this command to remove any Skype start-up entries:

```
sudo update-rc.d -f skype remove
``` That's for system-wide background processes that get started during system boot or shutdown, e.g. the GNOME login manager.

Skype would never ever be listed in there. Can't be listed in there.

If anything it would be in some desktop's autostart setting or maybe inside ~/.xinitrc or some such place.

---

### Post by scorp123 on 2009-11-27
> **laurent255 said:**
>  * sudo apt-get remove --purge skype
 * sudo reboot
=> at last! skype did not auto start

i then reinstalled skype, and it starts again automatically .... Of course.

De-installing and re-installing a misbehaving program **is Windows-thinking.** Here this will **NOT** work. Even if you remove a program its settings inside your /home directory will survive. So next time you reinstall the program again, the old (bad?) settings become active again and you're back to square #1.

I'd check the GNOME preferences:

***System > Preferences > Startup Applications***

Make sure Skype isn't listed to be started when you login to GNOME. Also, sometimes people add stuff manually to files such as **~/.xinit** or **~/.xinitrc** and then forget about that. So you should check that you don't have any such file. If you have: Check what's inside. These are (ancient?) X11 startup scripts that would auto-start things as soon as you have a GUI session. They're considered a bit obsolete these days (because e.g. GNOME and KDE have their own more elegant mechanisms of auto-starting applications) but they are still being executed by X11 when and if encountered ... So make sure you don't have any such files and no unwanted entries in them.

---

### Post by anonSam on 2009-11-27
Thanks for the more clear-cut explanation of that command. I couldn't really find a good explanation when I searched before; just knew that it's worked well for me to remove other programs from the start-up.

---

### Post by scorp123 on 2009-11-27
> **anonSam said:**
> I couldn't really find a good explanation when I searched before Did you try the manual?
```
man update-rc.d
```
> 
" ... *update-rc.d*  updates  the  System  V  style init script links /etc/rcrunlevel.d/*NNname* whose target is the script */etc/init.d/name*.  **These links are run by init when it changes runlevels; they are generally used to start and stop [B]system services such as daemons**[/B] ... "



---

### Post by anonSam on 2009-11-28
scorp123: Thanks! Learned something new.

---

### Post by laurent255 on 2009-11-28
laurent@laurent-laptop:~$ ls .config/autostart/
blueman.desktop           empathy.desktop                 gwibber.desktop
bluetooth-applet.desktop  evolution-alarm-notify.desktop  vino-server.desktop
dropbox.desktop           gnome-at-session.desktop
laurent@laurent-laptop:~$ ls /etc/xdg/autostart/
at-spi-registryd.desktop
blueman.desktop
bluetooth-applet.desktop
gdu-notification-daemon.desktop
gnome-at-session.desktop
gnome-keyring-daemon.desktop
gnome-power-manager.desktop
gnome-screensaver.desktop
gnome-settings-daemon.desktop
gnome-settings-daemon-helper.desktop
gnome-volume-control-applet.desktop
gwibber.desktop
indicator-applet.desktop
jockey-gtk.desktop
nm-applet.desktop
polkit-gnome-authentication-agent-1.desktop
print-applet.desktop
seahorse-daemon.desktop
update-notifier.desktop
user-dirs-update-gtk.desktop
vino-server.desktop
laurent@laurent-laptop:~$

---

### Post by blueridgedog on 2009-11-28
It is not there, so perhaps it was remembered as a start up application.  I would try the following:

Close all programs then
System - Preferences - Startup Applications, second tab, Check to remember settings, then close and reboot.

Repeat, but uncheck.  I have seen time when an application is remembered and needs to be cleared by having it "remember" a blank session.

---

### Post by scorp123 on 2009-11-28
> **blueridgedog said:**
> It is not there, so perhaps it was remembered as a start up application.  I would try the following:

Close all programs then
System - Preferences - Startup Applications, second tab, Check to remember settings, then close and reboot.

Repeat, but uncheck.  I have seen time when an application is remembered and needs to be cleared by having it "remember" a blank session. +1

Just happened to my wife's dad as well. In his case both Firefox and Skype insisted on auto-starting ... very odd.

---

### Post by laurent255 on 2009-11-28
> **blueridgedog said:**
> It is not there, so perhaps it was remembered as a start up application.  I would try the following:

Close all programs then
System - Preferences - Startup Applications, second tab, Check to remember settings, then close and reboot.

Repeat, but uncheck.  I have seen time when an application is remembered and needs to be cleared by having it "remember" a blank session.

Thanks blueridgedog !! that was the fix !

---

### Post by bingasedu on 2010-06-07
Just wanted to add some info based on my similar experience with this problem.  I went round and round with Preferences->Starup Applications->Options, shutting down skype and clicking Remember Currently Running Applications, following the suggestions in this thread and others, etc.  That ultimately led to a situation where I had 3 instances of skype automatically starting up, but skype was never listed in Preferences->Startup Applications->Startup Programs.

Eventually I found a very simple solution and a possible explanation for why skype does not show up in the Startup Programs list.  It turns out that when you close the skype login window you haven't actually shutdown skype.  At the top of the screen you will still see a small skype icon.  You must click on that icon and select close to shutdown skype.  In addition, I found that the saved session files under .config/gnome-sessions/saved-sessions contains error messages about the skype.png icon, and I suspect that a bad skype icon is why skype does not show up in the Startup Programs list.

---

