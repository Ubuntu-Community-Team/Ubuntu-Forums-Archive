---
title: "Newbie TOTALLY confused about gnome, compiz, metacity and emerald"
date: 2010-06-09
forum: General Help
---

### Post by Istrebitel on 2010-06-09
Greetings.

I want to have an eyecandy desktop with Ubuntu. What i would like to achieve is:
- transparency (like here [http://www.youtube.com/watch?v=VFqj2hS_0iQ](http://www.youtube.com/watch?v=VFqj2hS_0iQ))
- cool glass like effects (link above)
- stylish looking, not "office" looking

I was very statisfied with KDE looks (Ghost theme, others...) but it was too buggy overall to use it. So i went to Ubuntu. Now the girl in the link above states you can make a nice desktop and she has such, but i cant achive that. moreover, while trying, i got hilariously confused and frustrated.

**First question.**

What is compiz, gnome, metacity and emerald, how do they relate to each other, to X server, which are mutally exclusive which are not?

It began when i started to look for themes. Following the girl's tutorial, i thought i have a compiz enabled system now so i can install compiz themes. But the themes in compiz folder on this site (gnome-look.org) were NOT welcome by my appearance menu. they had .emerald extension.

I googled and digged. I found out that emerald is a replacement for metacity. Okay i installed that. But:
a) there is no guide in how to make it boot on startup or be used by default
b) it made my panels unstable (freezing) - the buttons of opened windows would froze and i had to blindly click them to find different windows underneath
c) it didnt do what it showed (theme showed glossy black transparent look yet only borders were changed when i applied it)

I've read alot on the webs and now i am even more confused:
a) some people state you should add compiz --replace to autorun to use compiz instead of metacity
b) some people say you should add export WINDOW_MANAGER=/bin/compiz or something to the ~/.gnomerc file to use compiz instead of metacity, while previous is a wrong way
c) some people state compiz is a window manager while metacity is decorator, so compiz CANNOT replace metacity, but emerald is the one that does replace metacity
d) but then, isnt gnome the window manager? so does compiz replace gnome? why does it look so gnomish then???
e) either way, neither (tweaking gnomerc file, tweaking compiz_settings file, adding compiz --replace or this & emerald --replace to autorun) did work for me, most i got was an ability to install emerald window decorators. some of which didnt work properly (looked distorted) and that didnt change nothing more, everything else was controlled from appearance where i couldnt achive what i wanted at all.

So what is compiz, what is emerald, what is gnome and what is metacity? And what of them i need to achive the looks i want? And why are themes that are marked as "compiz" really emerald themes? if compiz != emerald?

**Second question**

I tried gnome themes then. They came in tar gz files and were recognised by Appearance Preferrnces. BUT! After i "Install"ed some, they stopped adding to the list! Instead, i had to chose one, and then configure it! But then, if the theme showed -ox buttons on the right of the window, but i chose the buttons that should be on the left side of the window, the buttons would move to the right. So, choosing New wave, then customising it by choosing everything of "ambiance" inside made an ambiance theme with reverse order of buttons in the header! 
This is SOOOOOOO Confusing! And neither theme offered me to choose something about transparency. I cannot achive what i want (glossy glass look, transparency in console etc) Nor i can add any more themes - the Appearance Preferences "eats them" (meaning you cant install them again - would give an error) but they dont appear in the list - you have to "configure" existing theme! W T F ?!?!?

How to properly install themes for gnome, and how to achive transparency and well, i said it enough times now what :) 

Thanks in advance!

PS: Now after i am sure i backtracked everything i did while trying emerald (removed all created files and undid all changes) i am back to boring interface, but! It takes top panel (with application-places-system and stuff, i merged them to one) 10-20 seconds to appear after boot! Can i get it back? I mean, before it was showing very fast after boot, right after the drum sound and now i have to wait for it to appear (i can even work with those applications that are launched from previous session, but panel is not yet there...)

---

### Post by Istrebitel on 2010-06-10
The more i read the MORE i get confused. Just what is happening. Why do people say in guides "install this do that and you have a cool interface" i do it and get nothing like that. Is emerald not supported on 10.04 or not? .... I dont think i am the only one who was though this, i mean, who wanted to "pimp" his Ubuntu 10.04? :confused:

---

### Post by limestone on 2010-06-10
> **Istrebitel said:**
> Greetings.

I want to have an eyecandy desktop with Ubuntu. What i would like to achieve is:
- transparency (like here [http://www.youtube.com/watch?v=VFqj2hS_0iQ](http://www.youtube.com/watch?v=VFqj2hS_0iQ))
- cool glass like effects (link above)
- stylish looking, not "office" looking

I was very statisfied with KDE looks (Ghost theme, others...) but it was too buggy overall to use it. So i went to Ubuntu. Now the girl in the link above states you can make a nice desktop and she has such, but i cant achive that. moreover, while trying, i got hilariously confused and frustrated.

**First question.**

What is compiz, gnome, metacity and emerald, how do they relate to each other, to X server, which are mutally exclusive which are not?

It began when i started to look for themes. Following the girl's tutorial, i thought i have a compiz enabled system now so i can install compiz themes. But the themes in compiz folder on this site (gnome-look.org) were NOT welcome by my appearance menu. they had .emerald extension.

I googled and digged. I found out that emerald is a replacement for metacity. Okay i installed that. But:
a) there is no guide in how to make it boot on startup or be used by default
b) it made my panels unstable (freezing) - the buttons of opened windows would froze and i had to blindly click them to find different windows underneath
c) it didnt do what it showed (theme showed glossy black transparent look yet only borders were changed when i applied it)

I've read alot on the webs and now i am even more confused:
a) some people state you should add compiz --replace to autorun to use compiz instead of metacity
b) some people say you should add export WINDOW_MANAGER=/bin/compiz or something to the ~/.gnomerc file to use compiz instead of metacity, while previous is a wrong way
c) some people state compiz is a window manager while metacity is decorator, so compiz CANNOT replace metacity, but emerald is the one that does replace metacity
d) but then, isnt gnome the window manager? so does compiz replace gnome? why does it look so gnomish then???
e) either way, neither (tweaking gnomerc file, tweaking compiz_settings file, adding compiz --replace or this & emerald --replace to autorun) did work for me, most i got was an ability to install emerald window decorators. some of which didnt work properly (looked distorted) and that didnt change nothing more, everything else was controlled from appearance where i couldnt achive what i wanted at all.

So what is compiz, what is emerald, what is gnome and what is metacity? And what of them i need to achive the looks i want? And why are themes that are marked as "compiz" really emerald themes? if compiz != emerald?

**Second question**

I tried gnome themes then. They came in tar gz files and were recognised by Appearance Preferrnces. BUT! After i "Install"ed some, they stopped adding to the list! Instead, i had to chose one, and then configure it! But then, if the theme showed -ox buttons on the right of the window, but i chose the buttons that should be on the left side of the window, the buttons would move to the right. So, choosing New wave, then customising it by choosing everything of "ambiance" inside made an ambiance theme with reverse order of buttons in the header! 
This is SOOOOOOO Confusing! And neither theme offered me to choose something about transparency. I cannot achive what i want (glossy glass look, transparency in console etc) Nor i can add any more themes - the Appearance Preferences "eats them" (meaning you cant install them again - would give an error) but they dont appear in the list - you have to "configure" existing theme! W T F ?!?!?

How to properly install themes for gnome, and how to achive transparency and well, i said it enough times now what :) 

Thanks in advance!

PS: Now after i am sure i backtracked everything i did while trying emerald (removed all created files and undid all changes) i am back to boring interface, but! It takes top panel (with application-places-system and stuff, i merged them to one) 10-20 seconds to appear after boot! Can i get it back? I mean, before it was showing very fast after boot, right after the drum sound and now i have to wait for it to appear (i can even work with those applications that are launched from previous session, but panel is not yet there...)
Compiz enables 3d effects, gnome is the desktop manager (panels, etc) metacity is the window controller (close, min, max and window titlebar) emerald is a alternative to gtk themes. To enable emerald press alt+f2 and type emerald --replace

---

### Post by limestone on 2010-06-10
Also. When you download gtk themes from ex gnome-look.org some themes are double packed so you have to un-tar some.. and some themes does'nt show in the mainlist I dont know why but you can change to them by go in to customize. The transparency thing is Compiz job so you'll have to install that and also, compiz needs graphic card drivers.

---

### Post by cradlethefall on 2010-06-10
When I try the emerald replace command, everything works fine. But if I close the terminal window I get a pop up saying the terminal is still running. I close iy anyway and instantly the emerald theme stops working.

Do I have to leave the terminal running the whole time to use the theme?

---

### Post by 3rdalbum on 2010-06-10
Compiz is a window manager. By default, Compiz uses the "Heliodor" window decorator, which uses Metacity themes. This is totally transparent to the user.

Emerald is a different window decorator. I wouldn't bother with Emerald, mostly because I've never seen a good original theme for it, and partly because it doesn't integrate with Compiz very well. It's also a bit of a pain to get going.

Certain themes for Gnome are just parts of a theme - for instance, a GTK theme is just for the controls (buttons, scrollbars, checkboxes and stuff). So you have to "Customise" the current theme in order to choose just a GTK theme. Or a Metacity theme. If the theme contains Metacity and GTK elements, then it will usually be selectable directly through the Appearance window without having to "Customise".

Transparency is not directly governed by themes. You'd need what's known as RGBA. RGBA is actually already enabled for programs that have been written to use it as long as you're using a theme based on the Murrine theme engine (sorry, this is getting more complicated, isn't it?). Gnome System Monitor has been written to be RGBA semitransparent, as has Gnome Terminal. You can get a plugin for Rhythmbox, Gedit and Eye Of Gnome to enable RGBA transparency in those applications.

There is an experimental thing where you can have RGBA for all GTK applications, but I'd highly recommend giving it a miss until Ubuntu 10.10.  I'm often finding programs that I have to add to the RGBA blacklist (that is, so they are rendered opaque) because they crash with transparency. I've even found that Openoffice.org will not work, even when blacklisted, with the experimental RGBA turned on.

So don't try it yet, it'll just frustrate you, because you're a new user. The Ubuntu developers should hopefully get the thing sorted out by the release of Ubuntu 10.10 and you'll be able to have your whole desktop running with transparency.

---

### Post by limestone on 2010-06-10
> **cradlethefall said:**
> When I try the emerald replace command, everything works fine. But if I close the terminal window I get a pop up saying the terminal is still running. I close iy anyway and instantly the emerald theme stops working.

Do I have to leave the terminal running the whole time to use the theme?
If you run something in a terminal you run it in a "shell" (inside the terminal). You have to use alt+f2 and in the run promt you enter emerald --replace. To have emerald start at startup you will go to System - Preferences - Startup Applications and create a new one with the command emerald --replace

---

### Post by Istrebitel on 2010-06-10
Please confirm if i got it right:

So the hierarchy goes like this:

Gnome -> (uses) Compiz -> (uses) Heliodor -> (can apply) Metacity skin

What is Metacity then? Another decorator? (i.e. same thing as Emerald)

----

If transparency is not enabled by theme, then where? How do i make my terminal semitransparent? I dont need all my applications transparent (hell no), i just want transparent bars and menus (but right now if i make top panel transparent, some of the addons sticked to it are still showing w/0 transparency so i have to turn it off)

And what do i do about latecoming panel and bugging dropdown menus? Is there a solution to fix it? It really starts to annoy when you have to blindy go through it...

---

### Post by rahilm on 2010-06-10
what happens when you disable compiz?? i've always believed metacity takes over.. maybe I am wrong.

about the transparent panels thing.. yeah its the second biggest issue i face while customising my desktop. The reason why the "addons" don't turn transparent when panel is transparent is simply because the theme doesn't allow them. If you want to do that, you have to choose another theme or edit that theme (i don't know how to do that)
AFAIK: dust, and clearlooks give 100% transparent panels..

---

### Post by rahilm on 2010-06-10
I think an app known as "Ubuntu Tweak" might help you. It makes many things easy to do on your computer. For instance, you can change the layout of title-bar (that left side buttons problem you are facing) with a click. You can enable transparent menus, some minor tweaks too. You have to google for it , I  forgot from where i downloaded it..

PS: don't bother with emerald.. it is pretty frustating (and slow). and it isn't so much eye-candyish you believe it to be.

---

### Post by Istrebitel on 2010-06-10
Okay. Simple. How do i get THIS:
[http://www.youtube.com/watch?v=gl-tmGfQrzs](http://www.youtube.com/watch?v=gl-tmGfQrzs)

Already terminal window is transparent with the basic theme.

---

### Post by rahilm on 2010-06-10
Although I don't have the patience of watching the entire video (slow connection), there is a pretty standard procedure for installing themes.
when you visit gnome-look.org or any other site and download gtk2 themes, you will get a .tar.gz or .tar.bz2 file. It is an archive, like zip or rar.
Right-click on desktop->Change desktop background->themes.
then drag the file (archive) to the window, a dialog will pop-up saying theme is installed. then you can see it on the list. Alternatively, you can click on "install" and then browse for you .tar archive.

Exactly same procedure goes for installing icon packs and cursor themes.

Post back if you run into problems.

---

### Post by Istrebitel on 2010-06-10
I do run into a problem. I cannot make a terminal window with transparent background but with opraque logo and text. Sorry i dont know how to explain it more simplier. I want a terminal window that has transparent background, but 100% visible letters and decoration. She has it in the video i shown.

All i managed is with CCSM opacity settings i can make whole terminal transparent but then letters are not visible since they are transparent too.

Also, a problem is that for an odd reason i am having periodically all my compiz effects returned to default (none) state. I have to enable them all (cube, 3dcube, rotation cube...) again. ANd i have to set in apperance "EXTRA" instead of "NONE" again. This happens i suppose during applying themes. May this be the case? OR why can it be happening? It only happens while i'm tweaking my ui. And - maybe the theme is the culprit, as it says the following "theme wont work correctly becasue you dont have package ubuntulooks installed". Maybe it tried to replace compiz with this? THere is no such package btw... at least aptitude doesnt know it

PS: My problem with blinking menus though solved by not using random effects, but specifying them. Now however fast i swtich through them, they dont bug anymore, but show immediately and correctly...

---

### Post by oldos2er on 2010-06-10
I didn't watch the whole video, but she probably changed the terminal's text color. Open gnome-terminal, click Edit, Profiles, Default (assuming you haven't changed the default), Edit, Colors.

---

### Post by Istrebitel on 2010-06-11
How embarassing. Transparency was there all the time... Thank you, works!

---

### Post by Istrebitel on 2010-06-11
Well then, looks like the thread is solved then... just comfirm someone that i am right:

**Gnome** is a **desktop manager**. It provides gui to **X-server**
**Desktop manager** uses a **window manager** to arrange windows on the screen. **Metacity** by default, and can be replaced with **Compiz**, that will by default consume current Metacity theme to look "almost identical" and will later assume any theme assigned with "appearance" menu in gnome settings.
**Window manager** uses **window decorator** to draw stuff around windows, i.e. borders, headers and buttons to minimise or close.
**Metacity** and **Compiz** use **gtk-window-decorator** by default. This window decorator can accept GTK themes (sometimes called also "gnome themes")
**Theme** actually is not something monolithic by itself, it consists of components i.e. icon set, decorator, color scheme, controls set, each may be chosen separately.
**Emerald** is one of window decorators. It is buggy on Ubuntu 10.04 (officially unsupported) and mostly shouldnt be used, even compiz developers tell so, and advise use of kde-window-decorator or gtk-window-decorator. Emerald themes are also sometimes called "Compiz themes".

Theme containing sites like gnome-look.org are not correctly cataloguing their themes (or users are not correctly enlisting their themes). Thats why there can be problems with theme installation:
a) "Metacity themes" are essentially "GTK themes" or themes for gtk decorator and gtk controls.
b) "Compiz themes" are essentially themes for emerald decorator
c) Sometimes people pack themes in an archive that contains theme information and correct folder arrangement, that allows it to be comsumed by "install" function of appearance menu...
d) Sometimes they dont. They will either pack archive multiple times (tar.gz in tar in zip) or pack multiple theme variants in one (2xtar.gz in tar.gz) in which case you need to extract the last archive (containing 1 theme) and then feed it to the appearance menu.
e) Transparency of windows or menus can be achived from CCSM, and transparency of individual parts of windows can be achived in preferences of said windows, for example gnome-terminal has such options. 

If using random animations in CCSM for drop down menus, they start to lag (at least for me). they dont fully display and i have to "touch" the menu entry for it to show onscreen. This is cured by not using random animations but specifying them specificly for those menus.

PS: THis article helped too [http://ubuntulinuxtipstricks.blogspot.com/2008/12/compiz-emerald-metacity-what.html](http://ubuntulinuxtipstricks.blogspot.com/2008/12/compiz-emerald-metacity-what.html)

---

### Post by oldos2er on 2010-06-11
Emerald is not buggy for me on 10.04, FWIW.

Edit: Metacity can do some compositing too. See [http://stillstup.blogspot.com/2008/10/transparency-in-gnomemetacity.html](http://stillstup.blogspot.com/2008/10/transparency-in-gnomemetacity.html)

---

