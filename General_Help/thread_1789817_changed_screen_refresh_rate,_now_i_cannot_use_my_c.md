---
title: "changed screen refresh rate, now i cannot use my computer"
date: 2011-06-24
forum: General Help
---

### Post by Archy1987 on 2011-06-24
Hello. I changed screen refresh rate to 75 hz (please dont ask why i did it, i dont know), and now when i turn on my computer i get this - [http://www.bildites.lv/images/qzl1bn4s64z0r8eglbc7.jpg](http://www.bildites.lv/images/qzl1bn4s64z0r8eglbc7.jpg)
And the screen is stucked, nothing happens. How to fix it ?

---

### Post by Archy1987 on 2011-06-24
Dont know what to do - reinstll ubuntu or fix this problem

---

### Post by LordNeo on 2011-06-24
Your best chance is to boot in recovery mode and reconfigure the screen.
I would also advice to delete your xorg conf file and reboot (it will be created back with some optimal configuration) but that will require you to use console and we want to keep it simple :P

---

### Post by Grenage on 2011-06-24
I have no idea where the settings for refresh rates are stored, nor do I know how to overwrite them.  You can use xrandr to set modes, but I'm not sure if that's possible unless x is running.

I could probably give you a basic xorg.conf which would get you up and running, but there is bound to be a better solution.  If nobody suggests one, then please post the following information:

You'll probably need to press Ctrl-Alt-F1 to get a basic terminal up, when the screen is fuzzy.  Failing that, booting from an Ubuntu liveCD will work.

Your graphics card:
```
lspci | grep VGA
```

Your desired screen resolution.
Your monitor make and model.

---

### Post by Archy1987 on 2011-06-26
Well, this is how i fixed this problem - 
*If you don&#8217;t have access to your graphical ([GUI]("http://en.wikipedia.org/wiki/Gui")) desktop to delete these folders in [Nautilus]("http://en.wikipedia.org/wiki/Nautilus_file_manager") or you&#8217;re stuck at the login screen, drop to a terminal by hitting **CTRL + ALT + F1**, login to your account, and run this command:*
 [INDENT]***rm -rf .gnome .gnome2 .gconf .gconfd .metacity***
[/INDENT] *Get back to your GUI desktop by hitting **CTRL + ALT + _F7_**.*
 *Login and VOILÀ!  Just like the first time you ever logged into your Gnome desktop.*

---

