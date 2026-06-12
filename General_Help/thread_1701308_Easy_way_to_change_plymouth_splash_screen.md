---
title: "Easy way to change plymouth splash screen"
date: 2011-03-06
forum: General Help
---

### Post by cforput on 2011-03-06
I have read posts on here about how to change the Plymouth splash screen and all that I have found so far are solutions where you have to install software to "manage" themes. I'm application adverse and don't want to install an app just to change a graphic. Isn't there a file somewhere in Plymouth that is the splash screen graphic? I just want to use my own pic and replace the graphic file with the one of my choice. 

You used to be able to do this in splash. Can you do it in Plymouth or am I forced to install a theme manager? You know, something like:

copy MySplashScreen.jpg PlymouthSplashScreen.jpg

Done!

Sorry if this has been discussed before but I couldn't find it by searching.

---

### Post by dirty_harry on 2011-03-06
hi cforput,

I found the solution here:
[http://ubuntuforums.org/showpost.php?p=9166279&postcount=10](http://ubuntuforums.org/showpost.php?p=9166279&postcount=10)


But to select the proper background I had to copy my background.jpg with sudo to "/usr/share/backgrounds"! 

I also tried to provide a screenshot of my gdm-login-screen, but sadly ALT+Printscreen gives my an empty clipboard and those other solutions(scripts, fbgrab...) were just blank without the select background. All I can say is that on my lucid-laptop it works fine.

the screenshot things bugs me a bit...

anyway, have nice day :)

---

### Post by cforput on 2011-03-06
Hum, tried that but got the following error:

No protocol specifiedNo protocol specified
No protocol specified

(gnome-appearance-properties:7045): Gtk-WARNING **: cannot open display: :0.0
Cannot open display:

---

### Post by dirty_harry on 2011-03-06
I also get errors, nevertheless I'm able to switch or apply another color. My errors look a little different from yours:

```
~$ gksu -u gdm dbus-launch gnome-appearance-properties

(gnome-appearance-properties:1907): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
I/O error : No such file or directory
I/O error : No such file or directory
```

sorry, but for me it is working. I'm using lucid.

---

### Post by dirty_harry on 2011-03-06
ohoh, I think I miss understood what you wanted. Or I mixed up "splash screen" and gdm-login-background. Because I only changed my login-background.

but I found this, what is again not so easy but looks promising:
[http://gnome-look.org/content/show.php/Space-Sunrise+Plymouth+Splash?content=129678](http://gnome-look.org/content/show.php/Space-Sunrise+Plymouth+Splash?content=129678)

I had to choose to alternativ, not the deb-package. but hell yeah, it looks awesome!


I think to problem is that splashscreens are animated and that timing is important.

---

