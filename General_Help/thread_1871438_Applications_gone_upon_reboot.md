---
title: "Applications gone upon reboot"
date: 2011-10-28
forum: General Help
---

### Post by lostsoul1313 on 2011-10-28
I'm pretty new to ubuntu, I installed ubuntu and then the kde plasma desktop because I like playing with the different shells. everything was working fine, but for some reason now when I log out or reboot, any apps I installed are removed. for example I install visual boy advance via the terminal sudo apt-get install visualboyadvance and as soon as I log out or reboot, its gone and I can use the same command to install it again, as if it never existed. I'm deeply confused at this point. and re-installing applications every time I want to log out doesn't seem like an option lol

---

### Post by mansonfan78 on 2011-10-28
Are you sure the applications are gone and it's not just a problem with the launchers not being saved?  In order for the applications to disappear they would have to be uninstalled (which wouldn't be instantaneous).

---

### Post by lostsoul1313 on 2011-10-28
well by pretty new to ubuntu, I meant very new. I wouldn't know how to check if its the launchers not being saved, I just figured they were being uninstalled because apt-get lets me install them as if they never existed.

if you'll let me know how to check, I'll be sure to tell you if that's the problem or not.

---

### Post by mansonfan78 on 2011-10-28
After you install an app it should put a launcher (shortcut in Windows-speak) somewhere in your main menu.  Install an app (anything) and then look through your menu and sub-menus until you find it.  Then, log out and back in and look in the same place.

---

### Post by techvish81 on 2011-10-28
sometimes there are conflicts between kde and gnome, which can result in weird things,  so if u want to try kde,  get  kubuntu , it will be better,  

uninstall kde and see what happens,  if no further problems, u can do what I said above to try kde.

---

### Post by mansonfan78 on 2011-10-28
Just thought of something, if you install a gnome-based app while in kde that app may not show up in the kde menus (same is true of installing a kde-based app in gnome).  The app is still there and you could manually create a launcher for it.  Most of the time the isn't an issue but with some apps it's kind of funny this way.

---

### Post by lostsoul1313 on 2011-10-28
well.. I was reading the terminal intently while installing, and it seems that zsnes is removing my visualboyadvance and my pcsxr, and visualboyadvance is removing my zsnes... for some reason, I didn't notice until logging out, but apparently logging out isn't the issue... any alternatives to zsnes that can be easily installed? as it seems zsnes is the issue here

---

### Post by mansonfan78 on 2011-10-28
You could try bsnes ( [http://byuu.org/bsnes/](http://byuu.org/bsnes/)) or Snes9x ([http://www.snes9x.com/](http://www.snes9x.com/)) although I don't really know that much about them and couldn't tell how well they work.

---

### Post by lostsoul1313 on 2011-10-28
yeah thanks, I didn't know installing applications can uninstall other applications... I'm going to install snes9x-gtk, thanks I'll mark this as solved.

---

### Post by mansonfan78 on 2011-10-28
You're welcome.

---

