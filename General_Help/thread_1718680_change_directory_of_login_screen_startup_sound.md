---
title: "change directory of login screen startup sound"
date: 2011-03-31
forum: General Help
---

### Post by fisch246 on 2011-03-31
I have googled and googled... I probably haven't found anything because it seems people don't actually have a term for this sound. -__- However I'm not referring to "Gnome Login Sound" I'm referring to the login screen sound. Those 2 drum pats you hear when you start up Ubuntu, before logging in. I was using Macbuntu, and have switched back, however it never changed my login sound back to what it was suppose to be. I knew how to change everything else back, so i didn't just run a script with out knowing how to clean up after it, however this is the only thing I don't know how to do. It keeps looking into the macbuntu folder to get the sounds before i log in. Probably being able to simply set the sound theme in the login screen would fix this issue. I've tried using Ubuntu Tweak, but no such luck. If no one can't find a solution I'll just have to use the other folder from now on >.< However I'm quite certain there's a script somewhere, that I can edit. I just need to know where it's at.

---

### Post by andrewthomas on 2011-04-01
The sound that is supposed to play is 
```
/usr/share/sounds/ubuntu/stereo/system-ready.ogg
```this is actually a symbollic link to 
```
/usr/share/sounds/ubuntu/stereo/dialog-question.ogg
``````
system-ready.ogg -> dialog-question.ogg
```So you should be able to play whatever sound you want by changing the link to point to the file that you choose.
Then, if you want to return to the default just
```
sudo rm /usr/share/sounds/ubuntu/stereo/system-ready.ogg
sudo ln -s /usr/share/sounds/ubuntu/stereo/dialog-question.ogg /usr/share/sounds/ubuntu/stereo/system-ready.ogg
```

---

### Post by fisch246 on 2011-04-01
ah yes indeed, that's cool. When I played the file it played the correct sound. So which means some script was edited someplace that told it to look into the wrong folder. Like I said I know what folder it's looking into. which is "/usr/share/sounds/macbuntu/stereo" instead of it being the ubuntu folder. So I can always just switch out the dialogue-question file in the macbuntu folder and be done with it, but I was wondering where that file/script might be that tells it where to look. Thanks for the help :)

---

### Post by fisch246 on 2011-04-03
it'd be great if someone could point me to a script that's activated on startup, that points to the sound file, so i can edit it. Don't worry I'll be careful.

---

### Post by towheedm on 2011-04-03
You are referring to the system-ready.sound, the sound that plays when gdm login screen appears.
This sound is controlled by this file:
```
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop 
```

---

### Post by fisch246 on 2011-04-03
i found that file... double clicked on it, and it played the correct sound... the command it is using is correct... know what points to that file?

---

### Post by towheedm on 2011-04-04
Apparently, the theme is still set to use the macbuntu sound theme.  The login screen is run as user gdm.  So you need to change the sound theme that gdm is using.  This is set in the gconf database and you can change it with this command:
```

sudo -u gdm gconftool-2 --type string --set /desktop/gnome/sound/theme_name "ubuntu"
```This should restore your original drum beat.

You should report this as a bug to the developer.

---

### Post by fisch246 on 2011-04-04
thanks that fixed it :) I knew it was the theme, but i didn't know there was a command for changing the theme. I also didn't know the user was GDM.

---

