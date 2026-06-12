---
title: "change the number of steps of the volume control applet"
date: 2010-09-07
forum: General Help
---

### Post by sanderd17 on 2010-09-07
On my toshiba, there is a wheel that sends keystrokes to the OS to change the volume. This works fine with the volume widget in the notification area but the only problem is the step size. The widget regulates the volume from complete silence to 100% in only 10 steps. That means you can't smoothly get the volume up and I have to watch out that I don't scroll too far with my wheel.

Is it possible to change the stepsize to 1-2% (make 100 or 50 steps) instead of 10 steps of 10%?

Thanks,
Sander

---

### Post by fly-by-night on 2010-09-07
Quoted from [http://ubuntuforums.org/showthread.php?t=335780](http://ubuntuforums.org/showthread.php?t=335780)

"Open up Configuration Editor:
Applications -> System Tools -> Configuration Editor

Navigate to this setting:
/apps/gnome_settings_daemon/volume_step

Set it to whatever you want, I used 3. The number indicates percentage."

Edit: Alt+F2 then **gconf-editor** press enter - for the Configuration Editor.

---

### Post by sanderd17 on 2010-09-07
Thanks, I tried to find it in the gconf editor before but didn't look at gnome-settings-deamon.

Now I found it, a step of 2% is just good.

---

### Post by lucacerone on 2011-12-01
Hi, the volume_step settings disappeared in Ubuntu 11.10 using Gnome3...
Is there a way to modify this value in Gnome 3 now?
Thanks a lot for the help!
Luca

---

### Post by sanderd17 on 2011-12-01
I know the Gnome team is moving all settings from gconf-editor to dconf-editor. I looked for that setting, But I haven't found it yet.

Do tell me when you find it.

---

