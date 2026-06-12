---
title: "Ubuntu Dark Theme Problems: User, Application, or Theme Issue?"
date: 2009-10-24
forum: General Help
---

### Post by bgilbert on 2009-10-24
Hi,

I moved to a dark based theme in Ubuntu (gnome) a little while back, and I've run into a rather annoying issue quite a few times recently. This is that an application (apparently) imposes a background on their application, normally a very light color, and then (apparently) decides to use the OS font color when displaying fonts on top of that background, which in the case of a dark theme is normally very light as well, resulting in unreadable menus and whatnot.

A few examples of this I've run into recently is NClass, Qwit, and several others. I'm sure I'll run into many more as I use more of my applications. My real question here is this a:

1. User problem, i.e. something I have unwittingly done or something that I can personally fix.

2. Application problem, i.e. the developers didn't anticipate this problem and hard-coded background colors, and didn't bother hard-coding the font color.

-or-

3. Theme problem, i.e. I'm just using a theme that has some incorrect settings that would result in this behavior. (This has been consistent across several widely used themes I've tried, so I'm guessing not)

Also, if this is a user problem, then how can I fix this?

Thanks in advance!
Bryan

---

### Post by VCoolio on 2009-10-24
It's probably either an application problem (especially with apps that don't natively use gtk, like firefox or openoffice) or a theme problem (check that using another dark theme with more or less the same background / foreground settings). The apps you mentioned I don't know, so I can't say anything about that.
If it's an application problem, run that program with another theme (GTK2_RC_FILES=$HOME/.themes/yourtheme/gtk-2.0/gtkrc applicationcommand) or try to use config files (like userChrome.css with firefox). If it's a theme problem, hack into the gtkrc file.

---

### Post by fragos on 2009-10-24
It's an application issue which you can influence by tweaking the colors in the dark theme. This can be done in System-> Preferences-> Appearance-> Customize button-> Colors tab.

---

