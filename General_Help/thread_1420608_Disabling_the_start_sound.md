---
title: "Disabling the start sound"
date: 2010-03-03
forum: General Help
---

### Post by felix-leg on 2010-03-03
Where can I disable this sound which appears at Ubuntu loading screen (_before_ log in -  drum-beats)?
Do I need some GUI tool or edit a conf file?

---

### Post by karthick87 on 2010-03-03
Goto---->System----->Preferences----->Sound

And then goto Sounds tab and then click Login and choose Disabled..

---

### Post by Ebonhawke on 2010-03-03
Or, if you have Ubuntu 9.10

System - Preferences - Startup Applications 

Unclick 'Login Sound' :)

---

### Post by felix-leg on 2010-03-03
> **getyourkarthick said:**
> Goto---->System----->Preferences----->Sound

And then goto Sounds tab and then click Login and choose Disabled..

I told I don't mean this sound which plays after I log in, but this "global" one :(. I've completely switch off sounds in this tab and I still hear drums >.<

> **Ebonhawke said:**
> Or, if you have Ubuntu 9.10

System - Preferences - Startup Applications 

Unclick 'Login Sound' :)
There is no 'Login Sound' on the list...O_o And yes I have 9.10 :)

---

### Post by audiomick on 2010-03-03
> **felix-leg said:**
> I told I don't mean this sound which plays after I log in, but this "global" one :(. I've completely switch off sounds in this tab and I still hear drums >.<


There is no 'Login Sound' on the list...O_o And yes I have 9.10 :)
It is called "Gnome login sound". Still, I am not quite sure that this will stop the drums or just the music after entering your password.
I have that drum sound turned off on mine, but don't remember exactly what I did to get rid of it. I have all system sounds turned off in system> preferences> sounds, and the Gnome Login sound in system> preferences> Startup Applications de-selected.

---

### Post by felix-leg on 2010-03-03
> **audiomick said:**
> It is called "Gnome login sound". Still, I am not quite sure that this will stop the drums or just the music after entering your password.
On my list there is nothing contains a "sound" word or any similar one except "gnome-volume-control-applet" but this is rather not about login sound >_>

---

### Post by crichard on 2010-03-03
> **audiomick said:**
> 
I have that drum sound turned off on mine, but don't remember exactly what I did to get rid of it.

same here but try this,


[LIST=1]
[*]Goto terminal and type
[*]> 
sudo gedit /etc/gdm/custom.conf

[*]Enter your password
[*]Add this line > SoundOnLogin=false
[*]Save it
[*]Restart
[/LIST]

---

### Post by felix-leg on 2010-03-04
Still not working...

---

### Post by crichard on 2010-03-04
One more bad suggestion,

[LIST=1]
[*]Goto Synaptic Package Manager
[*]On that quick search enter ubuntu-sounds
[*]Pick that Package & uninstall it.
[*]Restart
[/LIST]
It won't kill your media files audio playback and all but it removes ubuntu-sounds package and also the event sounds on Gnome.
Experiment this & tell us a result.

---

### Post by VCoolio on 2010-03-04
The sound that plays is defined by this file:
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop
Edit it with sudo nano (commandline) or gksudo gedit, change the exec line.
The sound itself is in /usr/share/sounds/ubuntu/stereo, it's the one that is a symlink.
You can also install gdm2setup from launchpad.net, it's a gui login manager that enables customizing the new gdm.

---

### Post by audiomick on 2010-03-04
> **VCoolio said:**
> The sound that plays is defined by this file:
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop
Edit it with sudo nano (commandline) or gksudo gedit, change the exec line.
The sound itself is in /usr/share/sounds/ubuntu/stereo, it's the one that is a symlink.
You can also install [COLOR=Red]gdm2setup from launchpad.net[/COLOR], it's a gui login manager that enables customizing the new gdm.
I think maybe that is what I used to turn the sound off on mine.

---

### Post by hobo14 on 2010-03-04
This should get rid of it:

$ **sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false**

---

### Post by felix-leg on 2010-03-08
> **hobo14 said:**
> This should get rid of it:

$ **sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false**
Your method is a winer :mrgreen:! Thanks a lot :D.

---

