---
title: "No System Sound this Morning"
date: 2011-10-16
forum: General Help
---

### Post by Frantic_Earthling on 2011-10-16
I have just installed 11.10 on my Asus M70Vn. As of yesterday evening, sound, system sounds were working fine. This norming: no more system sounds. No login sound. 

However, "Sound Settings -> Sound Effect -> Choose an Alert Sound" work. Volume is up.

I'm posting the result of *pulseaudio -nC* and *aplay -l* 

Does the message *pa_pid_file_create() failed* mean anything useful?

Where should I look for a solution?

---

### Post by voldar on 2011-10-16
i am no expert but it sounds like a permission error have your tried deleting to file responsible and replacing it?

---

### Post by hansdown on 2011-10-16
Hi, Frantic_Earthling.

It's a regression.

Bug reports have been filed, as far back as, 2007.

Did you upgrade to your present os?

---

### Post by Frantic_Earthling on 2011-10-16
> **voldar said:**
> i am no expert but it sounds like a permission error have your tried deleting to file responsible and replacing it?

My apologies but i do not understand what you mean by "deleting to file responsible"

---

### Post by Frantic_Earthling on 2011-10-16
> **hansdown said:**
> Hi, Frantic_Earthling.

It's a regression.

Bug reports have been filed, as far back as, 2007.

Did you upgrade to your present os?

No, this is a fresh install. The sound has been working for the last two days following the install. It stopped this morning. That is, only system sounds. Audio/video play fine.

---

### Post by voldar on 2011-10-16
sorry i was thinking there might of been stale files from a upgrade have you done any recent updates that might of caused the problem?

under the txt att it said main.c: pa_pid_file_create() failed.
that sounded like a permission error to me since everything else is working related to sound
do videos play sound mp3s etc?

---

### Post by quequotion on 2011-10-16
scratch that, i was talking about something entirely off topic.

---

### Post by hansdown on 2011-10-16
> **Frantic_Earthling said:**
> No, this is a fresh install. The sound has been working for the last two days following the install. It stopped this morning. That is, only system sounds. Audio/video play fine.

Can you copy and paste this in a terminal?

```
grep pulse /var/log/messages
```

Post the output, and we may know more.

---

### Post by cottfcfan on 2011-10-16
Similar problem here.
I do have login sound, but once on the Desktop no system sounds appear to be working.
Again Music & Vid. play fine, and this is a fresh install.

Just an addition to this.
In Gnome 2 you had to tick a box in sound settings to enable system sounds.
In Gnome 3 this is missing.
Are system sounds even enabled by default?

---

### Post by Frantic_Earthling on 2011-10-16
> **hansdown said:**
> Can you copy and paste this in a terminal?

```
grep pulse /var/log/messages
```

Post the output, and we may know more.

I am afraid there is no "messages" file in /var/log.

What do you mean?

---

### Post by Frantic_Earthling on 2011-10-16
Voldar, yes I can play video audio and MP3.

---

### Post by voldar on 2011-10-17
Ok i am grasping at straws here but...
check sound preferences and make sure ubuntu sound theme is selected.
check alert volume in sound preferences
check start up appilcation preferences and make sure gnome login sound is checked.
click edit button on gnome login sound and make sure the path is correct

---

### Post by Frantic_Earthling on 2011-10-17
> **voldar said:**
> 
(1) check sound preferences and make sure ubuntu sound theme is selected.
(2) check alert volume in sound preferences
(3) check start up appilcation preferences and make sure gnome login sound is checked.
(4) click edit button on gnome login sound and make sure the path is correct

voldar, thanks for your suggestions, but as I said in my first post, I already checked (1) and (2).

As for (3), there is indeed an "Additional Startup Application Preferences" menu in 11.10 but it is empty and it is there only for you to fill it in as need arises. In other words, the default startup applications are not listed in it as they were up to 11.04 so you cannot remove or edit any pre-existing daemon. That is one of my problems as I do indeed remember that "login sound" used to be one of them.

So well, I can't check the path (4)! 

I checked the list of autostart programs in */etc/xdg/autostart* (see list below) and opened all programs having to do with sound. However I did not find anything related to "login sound".

at-spi-dbus-bus.desktop
bluetooth-applet.desktop
bluetooth-applet-unity.desktop
caribou-autostart.desktop
deja-dup-monitor.desktop
gdu-notification-daemon.desktop
gnome-fallback-mount-helper.desktop
gnome-keyring-gpg.desktop
gnome-keyring-pkcs11.desktop
gnome-keyring-secrets.desktop
gnome-keyring-ssh.desktop
gnome-settings-daemon.desktop
gnome-sound-applet.desktop
gnome-user-share.desktop
gsettings-data-convert.desktop
gwibber.desktop
jockey-gtk.desktop
nautilus-autostart.desktop
nm-applet.desktop
nvidia-autostart.desktop
onboard-autostart.desktop
orca-autostart.desktop
polkit-gnome-authentication-agent-1.desktop
print-applet.desktop
pulseaudio.desktop
pulseaudio-kde.desktop
telepathy-indicator.desktop
ubuntuone-launch.desktop
update-notifier.desktop
user-dirs-update-gtk.desktop
vino-server.desktop
zeitgeist-datahub.desktop

---

### Post by Frantic_Earthling on 2012-01-08
Here is the solution:

[http://ubuntuforums.org/showthread.php?p=11596804#post11596804](http://ubuntuforums.org/showthread.php?p=11596804#post11596804)

---

