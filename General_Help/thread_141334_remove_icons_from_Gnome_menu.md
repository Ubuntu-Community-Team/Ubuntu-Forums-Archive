---
title: "remove icons from Gnome menu?"
date: 2006-03-08
forum: General Help
---

### Post by ed_agamemnon on 2006-03-08
I've got a bit sick of Gnome being slow on my laptop (celeron 2.4ghz; only 256MB RAM) so I'm using Blackbox for the moment, which is great and all, only I still want to use Gnome Panel... Would it be possible for me to disable the icons from the 'Applications Places System' menu? - & would this have any noticeable performance boost?

maybe it's just a general Celeron sluggishness? - it seems a ton of people are suffering with these processors...

---

### Post by Stealth on 2006-03-08
Hmm...I know in Fluxbox you can use an app called [menumaker]("http://menumaker.sourceforge.net/") to get the Gnome menu entries in its own menus, have you tried that?

---

### Post by IYY on 2006-03-08
It's certainly possible, since I've done it once. I also remember I didn't have to edit any files, it's an option that can be selected via GUI. I imagine it must be hidden somewhere in the Configuration Editor. Removing the icons would not really make anything faster, but it would appear to do so because there is a slight delay between when you open the menu and when the icons show. If there are no icons, this delay would not exist, and it would appear to be faster.

By the way, you may get a big boost if you disable antialiased fonts and switch to a lighter theme, like Mist. I'm running Gnome on a system nearly 5 times slower than yours (~400 MHz, 128 MB of RAM), and it's not so bad.

---

### Post by ed_agamemnon on 2006-03-08
Where can I switch to anti-aliased fonts? As for running Mist, I already am :(

I'll have a browse through the Config. Editor and see what I can find... It's really a little ridiculous that opening to programs at the same time takes so long; that any more than 3 firefox tabs makes minimising and maximising very clunky; that Gnome Terminal takes almost 6 seconds to load... etc etc. I figure there's got to be something rather drastically wrong somewhere, I just have to find out what :)

Menueditor doesn't have a .deb anywhere yet so I'll have a go at compiling it later - if I'm feeling brave enough... compiling tends to make me so so angry!

---

### Post by ed_agamemnon on 2006-03-08
Ok, tried the anti-aliasing... didn't seem to make much difference. I think nautilus is my big problem, whenever it's running, my system crawls. - Kill it and the speed increase is just enormous! too bad ROX is so ugly *humpf* :(

---

### Post by IYY on 2006-03-10
Here's a suggestion that might work:

Don't use Gnome. Try FluxBox or IceWM instead. If you find life difficult without a desktop and gnome-panel, you can still use them in another window manager. Just add them to the startup.

Another option is XFCE, though it's not quite as light as the others.

As for minimizing and maximizing: there is an option that makes it faster in the configuration editor. However, it will also make the windows move and resize in wireframe mode (I actually like that, but some people got used to the new opaque mode). 

Also, I don't like gnome-terminal. Eterm, aterm and xterm are all better. I prefer aterm.

BTW, if you're still having problems removing the icons from the menus: system > preferences > menus and toolbars

---

