---
title: "How To Stop An Application Autostarting In Gnome And Xfce4?"
date: 2010-01-16
forum: General Help
---

### Post by Mark76 on 2010-01-16
It seems that the two DEs read from the same damned autostart file as no matter how much I edit the start up menus for each the applications I want to autostart in Gnome but not in Xfce4 just ignore me and bloody well autostart in Xfce4 anyway.

And, yes, I did untick Gnome services :-x ](*,)

---

### Post by Brandon Williams on 2010-01-17
Both gnome and xfce use the same method to prevent an autostart app from being run. The set its Hidden attribute to true. If you want the startup app to be run in one environment but not the other, then you have to edit the .desktop file by hand.

Look for the appropriate .desktop file in your ~/.config/autostart directory. If it doesn't exist there, then it's probably in /etc/xdg/autostart. If that's the case, copy it from /etc/xdg/autostart into ~/.config/autostart.

Once you've identified the correct .desktop and ensured that it is in your own ~/.config/autostart directory, open it with your favorite editor. There are two properties that can be used to indicate which environment the application should be run in: OnlyShowIn and NotShowIn. The first is used to provide a whitelist of one or more environments that the application should be run in, and the second provides a blacklist of environments that the application should not be run in.

Here's an example. In my environment, I want conky to run in Xfce but not in Gnome. My .desktop file looks like this:
```
$ cat ~/.config/autostart/conky.desktop
[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=Conky
Comment=Start conky display
Exec=conky
X-GNOME-Autostart-enabled=false
NotShowIn=GNOME;
```

I could also replace the NotShowIn line with 'OnlyShowIn=XFCE;' to get the same effect. Notice that there is also an X-GNOME-Autostart-enabled property. I can't remember at the moment why they are both there in my file. It could be that Gnome requires it in order to disable the autostart. I know that XFCE respects the other two properties.

---

### Post by Mark76 on 2010-01-17
It doesn't work.

No matter what I try AWN keeps autostarting in Xfce4.

I am sick and tired of it not respecting my settings.

---

### Post by Mark76 on 2010-01-17
Show me how I'd write xcfe4 if I wanted an application to show/not show in that environment.

---

### Post by Brandon Williams on 2010-01-18
When specified in an OnlyShowIn or NotShowIn property, refer to is as XFCE ... all caps, no '4'.

Are you absolutely certain that AWN is starting do to the autostart item? Is it possible that it's showing up in your Xfce session cache? Does it work to disable it from the 'Session and Startup' dialog? If that works, then it's not a session cache problem and the change to the .desktop file should be enough.

---

