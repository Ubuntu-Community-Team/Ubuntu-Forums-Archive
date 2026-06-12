---
title: "Start up Sounds"
date: 2010-04-14
forum: General Help
---

### Post by RastaCalavera on 2010-04-14
What is the best way to disable start up sounds? I hate being in a quiet place and having the start up sound go off on my computer. I've tried muting before shutting down and that works 40% of the time when i start up again. I do dual boot os, so will changing something in Ubuntu mess with mint or vice versa? Thanks!!

---

### Post by -humanaut- on 2010-04-14
System-->Preferences-->Sound

---

### Post by dwarfolo on 2010-04-14
Disable "GNOME Login Sound".

System -> Preference -> Startup applications

---

### Post by auh2o on 2010-04-14
> **dwarfolo said:**
> Disable "GNOME Login Sound".

System -> Preference -> Startup applications

That won't help if it's the idiotic drum sound at the login screen he's talking about. I've found NO way to disable it - your tip or editing the sound preferences included - short of renaming the sound file itself.

The file is

```
/usr/share/sounds/ubuntu/stereo/dialog-question.ogg
```Renaming it to whatever will remove this horrible login sound.

---

### Post by dwarfolo on 2010-04-14
dho!!
I've always found that "drums sound" somehow funny ... stupid, but funny :P

---

### Post by RastaCalavera on 2010-04-14
> **auh2o said:**
> That won't help if it's the idiotic drum sound at the login screen he's talking about. I've found NO way to disable it - your tip or editing the sound preferences included - short of renaming the sound file itself.

Yeah that is what I am talking about. I hate it when i am in the library and it goes off and forty people look at me like ,"WTF?!!". Thanks a million I will give it a try!

---

### Post by nuchdog on 2010-04-16
try this

1st: alt+F2 and run gconf-editor to open the editor
2nd: untick the active key in order to disable the login ready drums sound in /apps/gdm/simple-greeter/settings-manager-plugins/sound/
3rd: must reboot

This is courtesy of nanonils in another thread

---

### Post by cosmicsync on 2010-05-08
> **nuchdog said:**
> try this

1st: alt+F2 and run gconf-editor to open the editor
2nd: untick the active key in order to disable the login ready drums sound in /apps/gdm/simple-greeter/settings-manager-plugins/sound/
3rd: must reboot

This is courtesy of nanonils in another thread


Thanks to nuchdog, and nanonils from the other thread. 

When I simply ran gconf-editor, uncheck the key and rebooted, I still had the sound, and the key was no longer uncheck. I ran 'sudo gconf-editor' from a command window instead, unchecked the key and rebooted, and this time the drum sound was gone and the key was still unchecked. 

I'm fairly new to Ubuntu, so I don't know if I need to configure gconf-editor to run as root without the sudo command, but hopefully this helps others who may have had the same problem and not thought to use sudo.

---

### Post by dirkvs on 2010-06-21
None of the above worked for me on Ubunto 10.04.

However, this did work:

Click on system/administration/login screen
Click Unlock
Enter the root password (a few times)
Untick the box that says Play Log-in sound

That's it!

---

