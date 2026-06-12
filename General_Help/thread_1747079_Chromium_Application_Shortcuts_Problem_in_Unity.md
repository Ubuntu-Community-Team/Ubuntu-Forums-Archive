---
title: "Chromium Application Shortcuts Problem in Unity"
date: 2011-05-02
forum: General Help
---

### Post by daz4126 on 2011-05-02
Hi,

I often use the option in Chromium to create 'application shortcuts'. These are instances of Chromium that make a website look more like an app by not including most of Chromium's toolbars. I use it for gmail and google docs and spreadsheets and calendar.

In 11.04 I have set up Desktop launchers and copied them across to the Launcher (what an odd way to add something to the launcher, why no right-click 'add launcher' option?)

The problem is that the launcher thinks all these apps are chromium (which they are really, but I would like them to be seen as separate apps). If I minimize my gmail window, a little triangle appears next to the chromium icon, not the gmail icon. To get the window back, I have to click on the Chromium icon. Clicking on the gmail icon launches a new instance of it (also tied to the Chromium icon).

Anybody got any ideas of how I can avoid this or is it a bug?

cheers,

DAZ

---

### Post by Joruus on 2011-05-03
Hi

I have the same problem with chrome apps :(

---

### Post by tushantin on 2011-05-06
I'm having the same problem. I start Chromium, but on Unity it says I'm actually using an application shortcut called "Deviantart Muro" (which I created long ago). No proper Chromium icon. I'm thinking of uninstalling the application shortcut, but I have no idea where to find it...

EDIT: Okay, so from the home folder I went to .local/share/applications, and there found the .desktop files of the application shortcuts, thus deleting them. Quick fix, but not a good one. :( You use your shortcuts, but hey, the icon's back!

---

### Post by daz4126 on 2011-05-07
I've found another place this happens.

Try opening a file window, then minimize it. Where does it go?

Now look at the Home button at the top of the launcher - there it is! It must get sent there because they both use Nautilus, but it doesn't make sense that minimized windows are found on a button marked 'home folder'.

This is both counter-intuitive and unusable. How do I go about filing a bug?

DAZ

---

### Post by daz4126 on 2011-05-07
> **tushantin said:**
> I'm having the same problem. I start Chromium, but on Unity it says I'm actually using an application shortcut called "Deviantart Muro" (which I created long ago). No proper Chromium icon. I'm thinking of uninstalling the application shortcut, but I have no idea where to find it...

EDIT: Okay, so from the home folder I went to .local/share/applications, and there found the .desktop files of the application shortcuts, thus deleting them. Quick fix, but not a good one. :( You use your shortcuts, but hey, the icon's back!

I'm glad you sorted it out tushantin!

You're right though, the fix won't work for me because I WANT the extra shortcuts - I just want them to be recognized as separate apps in the launcher though!

DAZ

---

### Post by filipe_aguiar on 2011-05-09
This is, aparently, a bug in chromium.

It seems that the browser doesn't tell the right info to the window manager (unity, in this case). I'm having the same problem.

You can keep an eye opened to this topic:
[http://code.google.com/p/chromium/issues/detail?id=20587](http://code.google.com/p/chromium/issues/detail?id=20587)
Where the chromium devs are discussing the same issue.

---

### Post by daz4126 on 2011-05-31
Ahhh, good spot filipe_aguiar ... I just assumed it was Unity at fault, but I've since found out that Cairo Dock behaves the same way (obviously since it is Chromium that isn't registering the application shortcuts properly). They still don't seem to have sorted it out, I hope they do soon!

cheers,

DAZ

---

### Post by filipe_aguiar on 2011-09-09
Still waiting for an correction.

In the end, this is a bug in Unity or bamf, not in chromium (it was a bug in chromium too, but is now fixed).

I hope that this could be fixed. Too much time has passed and still not a single correction for this ANNOYING BUG!

---

### Post by t.rei on 2012-06-12
*edit* Actually it is fixed - it just took me a while to figure it out:

Here's a working launcher in $HOME/.local/share/applications/
(obviously you need to replace the icon-line with a working one).

```

[Desktop Entry]
Name=Google Kalender
Exec=google-chrome --app=https://www.google.com/calendar
StartupNotify=true
Terminal=false
Type=Application
Icon=/home/t.rei/.local/share/my_icons/my_cool_google_calendar_pixmap.png
StartupWMClass=www.google.com__calendar

```

---

