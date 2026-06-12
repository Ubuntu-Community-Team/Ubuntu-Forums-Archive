---
title: "Mail &amp; Chat Notification Sounds Not Working"
date: 2010-07-20
forum: General Help
---

### Post by kernelles on 2010-07-20
I'm running 10.04 64 bit, and my mail & chat notification sounds are not working. I have enabled/turned up the sound notification settings in Empathy and Evolution, as well as in System/Preferences/Sound, but no difference. My sound works for everything else, including system notifications for when I open a program, etc.

Thanks,

Les.

---

### Post by valbaca on 2010-07-20
In System/Preferences/Sound, is the theme set to "No Sounds"?

---

### Post by kernelles on 2010-07-20
> **valbaca said:**
> In System/Preferences/Sound, is the theme set to "No Sounds"?

No, it is set to "Ubuntu."

---

### Post by valbaca on 2010-07-20
Try:
[http://ubuntuforums.org/showthread.php?t=1194501](http://ubuntuforums.org/showthread.php?t=1194501)

---

### Post by kernelles on 2010-07-27
> **valbaca said:**
> Try:
[http://ubuntuforums.org/showthread.php?t=1194501](http://ubuntuforums.org/showthread.php?t=1194501)

Thanks, Valbaca. I tried this, but it still didn't work. Any other ideas?

---

### Post by philinux on 2010-07-27
> **kernelles said:**
> Thanks, Valbaca. I tried this, but it still didn't work. Any other ideas?

In evolution double check the settings in Edit>Plugins>Mail notifications.

I had to substitute a .wav file to get this to work by the way, ogg files either wouldn't play at all or sounded like loud static. 
There are a load of wav file in here. /usr/lib/openoffice/basis3.2/share/gallery/sounds/

And check Edit>prefs>Mail Prefs.

---

### Post by kernelles on 2010-07-27
> **philinux said:**
> In evolution double check the settings in Edit>Plugins>Mail notifications.

I had to substitute a .wav file to get this to work by the way, ogg files either wouldn't play at all or sounded like loud static. 
There are a load of wav file in here. /usr/lib/openoffice/basis3.2/share/gallery/sounds/

And check Edit>prefs>Mail Prefs.

Thanks, just tried it, but still nothing. The file I chose plays when I preview it in settings, but not when I receive a message.

---

### Post by philinux on 2010-07-27
> **kernelles said:**
> Thanks, just tried it, but still nothing. The file I chose plays when I preview it in settings, but not when I receive a message.

You might need to log out and back in or even reboot.

---

### Post by kernelles on 2010-07-27
> **philinux said:**
> You might need to log out and back in or even reboot.

That did it! Thanks!!!

---

