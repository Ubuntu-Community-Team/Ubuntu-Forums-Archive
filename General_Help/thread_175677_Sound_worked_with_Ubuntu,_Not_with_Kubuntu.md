---
title: "Sound worked with Ubuntu, Not with Kubuntu"
date: 2006-05-13
forum: General Help
---

### Post by deadyeti on 2006-05-13
Recently I installed Ubuntu, and everything was working well but Im not too fond of Gnome.  So I went and installed KDE in Ubuntu which took me a while but I figured it out with the help of these forums.  However when i installed KDE I found that the only time my sound worked was with Teamspeak.  So I decided to install Kubuntu figuring I screwed something up while installing KDE on Ubuntu 5.10.  Well I am having the same problem in Kubuntu with sound, it only works in Teamspeak and with system sounds.  Im not sure what could be wrong, I messed with Kmix but nothing seems to work.  Maybe someone here has some sort of help for this Linux learner.

-Yeti

---

### Post by tarakan on 2006-05-13
[QUOTE=deadyeti]Recently I installed Ubuntu, and everything was working well but Im not too fond of Gnome.  So I went and installed KDE in Ubuntu which took me a while but I figured it out with the help of these forums.  However when i installed KDE I found that the only time my sound worked was with Teamspeak.  So I decided to install Kubuntu figuring I screwed something up while installing KDE on Ubuntu 5.10.  Well I am having the same problem in Kubuntu with sound, it only works in Teamspeak and with system sounds.  Im not sure what could be wrong, I messed with Kmix but nothing seems to work.  Maybe someone here has some sort of help for this Linux learner.

-Yeti[/QUOTE]

Well, if you're trying to play a restricted media format like mp3 or .avi, mpeg and so on, then:

- Install Synaptic (optional)
- in the repository list check all universe, multiverse, which are unchecked by default and click on "Reload" to get the current list of packages
- install kde-multimedia package and all its dependancies (they will be automatically selected after you have checked the main package)
- install all gstreamer packages, excluding the "dev" packs
- upgrade to the latest versions of AmaroK and Kaffeine
- (optional) install the xine engine and switch to it in Kaffeine and AmaroK

---

### Post by deadyeti on 2006-05-13
I will try that out, I cant even get sounds from programs like GAIM when I send IMs and stuff.  Audio CDs play but the volume is very very low even with volume all the way up

---

### Post by tarakan on 2006-05-13
Also make sure that you have enabled the sound system in Control Center > Sound and Multimedia. In the "System Notifications" section you can add the programs and sound events you want to receive. If the volume is too low - adjust the sliders in Kmix and raise the PCM slider. Don't forget to restart the sound server (Terminal > killall artsd) after you have installed the new packages.

Hope you'll get it running! Good luck! :)

---

### Post by deadyeti on 2006-05-13
Still nothing.  I guess I will have to use Gnome, everything worked there for me.  Kinda stinks.  I really liked KDE

---

### Post by Harold P on 2006-05-14
You could just be using the wrong sound output device. Just right click on the sound icon in the tray, and change the Master Channel.

---

