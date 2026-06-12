---
title: "close lid do nothing fail"
date: 2012-04-27
forum: General Help
---

### Post by TheShabz on 2012-04-27
Hi everyone,

With 12.04 out and the much awaited increased support for multiple monitors, I was stoked to finally be able to use my TV as my monitor and essentially "dock" my laptop with an external KVM (not a switch, just USB for the keyboard and mouse, HDMI for the tv.

Now, onto the issue. I have the power settings for lid close set to do nothing while on AC. With the lid open, everything works fine and the video feed gets sent to my TV. However, when I close the lid to tuck it away, I lose the feed to my TV. Opening the lid back up prompts me for my password, indicating that it did not "do nothing." What, if anything, am I doing wrong here?

Thanks in advance

---

### Post by collisionystm on 2012-04-27
Can you check the lights on your computer to see if its going to sleep? It sounds like even though you set it not to, its happening anyways

---

### Post by TheShabz on 2012-04-27
It looks like it does as the fan turns off. However, when i unplug the HDMI cable and close the lid, it stays active.

---

### Post by matt_symes on 2012-04-27
Hi

Monitor power saving ? Have you played with dpms ?

Open a terminal and type

```
xset -dpms
```

Then close the lid. Any change ?

Kind regards

---

### Post by TheShabz on 2012-04-27
No change

---

### Post by matt_symes on 2012-04-27
Hi 

Did you disable the screen saver lock screen ? Not sure if that's the problem but worth checking.

Can we also check the settings. Open a terminal and type
```

gsettings  list-recursively | grep power
```Post the results back here.

Kind regards

---

### Post by TheShabz on 2012-04-27
No change. What's throwing me off is that the settings work fine as long as I dont have my HDMI cable plugged in. When it's in, my computer screen is off and the TV is on, just as I need. Once the lid closes, the computer locks. When the HDMI cable is unplugged, the proper settings are applied and the computer does not lock. 

On a side issue, and not very important at this time but might be related, the sound output remains with the laptop speakers and does not go to the TV.

---

### Post by matt_symes on 2012-04-27
Hi

The last command posted was to see what your settings are, not to set anything. 

Can you rerun the command again and post the results back in your next post.

Kind regards

---

### Post by TheShabz on 2012-04-27
My apologies. it looked it like was setting the power properties to a profile.


com.canonical.indicator.power icon-policy 'present'
com.canonical.indicator.power show-time true
org.gnome.power-manager info-history-graph-points true
org.gnome.power-manager info-history-graph-smooth true
org.gnome.power-manager info-history-time 21600
org.gnome.power-manager info-history-type 'charge'
org.gnome.power-manager info-last-device ''
org.gnome.power-manager info-page-number 0
org.gnome.power-manager info-stats-graph-points true
org.gnome.power-manager info-stats-graph-smooth true
org.gnome.power-manager info-stats-type 'discharge-accuracy'
org.gnome.rhythmbox.plugins active-plugins ['artdisplay', 'audiocd', 'audioscrobbler', 'cd-recorder', 'daap', 'dbus-media-server', 'generic-player', 'ipod', 'iradio', 'mmkeys', 'mpris', 'mtpdevice', 'notification', 'power-manager']
org.gnome.settings-daemon.plugins.power active true
org.gnome.settings-daemon.plugins.power button-hibernate 'hibernate'
org.gnome.settings-daemon.plugins.power button-power 'interactive'
org.gnome.settings-daemon.plugins.power button-sleep 'suspend'
org.gnome.settings-daemon.plugins.power button-suspend 'suspend'
org.gnome.settings-daemon.plugins.power critical-battery-action 'hibernate'
org.gnome.settings-daemon.plugins.power idle-brightness 30
org.gnome.settings-daemon.plugins.power idle-dim-ac false
org.gnome.settings-daemon.plugins.power idle-dim-battery true
org.gnome.settings-daemon.plugins.power idle-dim-time 30
org.gnome.settings-daemon.plugins.power lid-close-ac-action 'nothing'
org.gnome.settings-daemon.plugins.power lid-close-battery-action 'nothing'
org.gnome.settings-daemon.plugins.power notify-perhaps-recall true
org.gnome.settings-daemon.plugins.power percentage-action 2
org.gnome.settings-daemon.plugins.power percentage-critical 3
org.gnome.settings-daemon.plugins.power percentage-low 10
org.gnome.settings-daemon.plugins.power priority 1
org.gnome.settings-daemon.plugins.power sleep-display-ac 1800
org.gnome.settings-daemon.plugins.power sleep-display-battery 1800
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'suspend'
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 3600
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'suspend'
org.gnome.settings-daemon.plugins.power time-action 120
org.gnome.settings-daemon.plugins.power time-critical 300
org.gnome.settings-daemon.plugins.power time-low 1200
org.gnome.settings-daemon.plugins.power use-time-for-policy true

---

### Post by Radical Thought on 2012-05-08
I am effected by this as well.

Possible  workaround:  In System Settings > Brightness and Lock switch off  'Lock'. The downside is that your system also cannot lock anymore after a  set time.

---

### Post by conualfy on 2012-05-08
I would report bugs for all of these, as I think that should be the way to a fix.

For locking the screen the bug report is here: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/995840/](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/995840/)

For the others, you should report bugs (if you know the package name, a simple way is to run in terminal "ubuntu-bug package", for instance "ubuntu-bug gnome-power-manager") and follow the on-screen wizzard.

---

### Post by TheShabz on 2012-05-08
I found that if I close the lid prior to plugging in the HDMI, everything works fine. Also, the sound does not automatically switch to the HDMI source, so you have to do that manually, which is no big deal.

---

