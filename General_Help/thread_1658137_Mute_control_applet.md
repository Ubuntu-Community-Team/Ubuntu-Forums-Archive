---
title: "Mute control applet"
date: 2011-01-02
forum: General Help
---

### Post by dougalkerr on 2011-01-02
Hi folks - I'm looking for a simple mute control icon or applet. My wife uses Skype regularly and is finding it frustrating that the only way to 'unmute' the sound is to have to open the sound applet to access the mute checkbox.

Is there a way to build an icon or an applet that can have an icon that activates/deactivates the mute control with one click?

If there is a guide to building applets somewhere that I can follow, I will have a go myself.

Thanks.

---

### Post by Gunman1982 on 2011-01-02
May I ask what she is trying to mute/unmute? the speaker? I sright click on the applet and check "mute" too much? Or is it about the mic?

If you are using pulseaudio as the sound server you can look into 'pacmd' start it in a console and type help and it'll tell you some info about possible commands
i.e.: 'pacmd set-sink-mute 0 1' mutes the first output sink (in my case the speakers)
You have to check which sink you want to mute and then write a script wich toggles the second argument between 0 and 1 for unmute and mute.

---

### Post by ajgreeny on 2011-01-02
**System ->Preferences ->Keyboard Shortcuts** can be used to make a keyboard shortcut, if one does not already exist for your system

---

### Post by JOHNNYG713 on 2011-01-02
Yes Very easy ! If you do not have a keyboard with a special button to  mute the volume, you can set the button that you want for it. Click on  the System menu> Preferences. Then click on the keyboard command  shortcuts. In the window that opens, click the Mute line heading Here.  Then press the button that lets you mute the sound, for example F12.  Finally, click the Close button. When you press the F12 key, the sound  is muted. Press again F12 to restore the volume. This is how mine is set  ! ):P

---

### Post by dougalkerr on 2011-01-03
Thanks everyone the Keyboard shortcut route in the Preferences menu has done the job.
I just needed a simple volume mute and the Super key + V has sufficed very nicely.

Thanks again.

---

