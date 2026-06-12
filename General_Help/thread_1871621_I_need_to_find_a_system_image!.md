---
title: "I need to find a system image!"
date: 2011-10-29
forum: General Help
---

### Post by hakermania on 2011-10-29
Hello, I really need to find the location of the 'Show Desktop' image being displayed when using the Alt-Tab function:
[IMG]http://i.imgur.com/Ls7rP.png[/IMG]

I've located the images:
/usr/share/icons/ubuntu-mono-(dark/light)/places/(128/16/22/24/32/48/64)/user-desktop.png but I'd changed all these files to other png images of the correct size (e.g. 128x128 went both to /usr/share/icons/ubuntu-mono-light/places/128/user-desktop.png and /usr/share/icons/ubuntu-mono-dark/places/128/user-desktop.png etc) and then I completely restart my PC and the same icon's still there.
I doubt the system creates the image dynamically on every boot but I've searched thoroughly all the system using the 'locate' and 'grep' commands with no luck...

Thanks...

---

### Post by jim_deadlock on 2011-10-29
If you're talking about your launcher icons, the images for those are specifically pointed to by your launcher files which you can edit - they are text files and have .desktop extensions, they are mostly found in these directories:

/usr/share/applications
~/.local/share/applications

If you open these in a text editor you can change the Icon= setting to any image path.

---

### Post by hakermania on 2011-10-29
Thanks for the info but I'm not talking about these :)
I was quite specific:
I need to know where the 'Show Desktop' icon (the one selected in the image on the 1st post) is located inside the system. I know where to find the firefox's and gedit's icons.

---

### Post by hakermania on 2011-10-29
I'll go crazy :PPPP
I changed all the images to one specific of the paths specified above and - all of a sudden - the image changed :)
[IMG]http://i.imgur.com/fIC4I.png[/IMG]
Ok, that's super weird, the image didn't change even when restarting.
I tried
1) Restarting nautilus
2) Restarting unity
3) Login-logout
4) Restarting Pc
and nothing worked. Now the icon's there and I cannot get how it did it...

I wish I knew what I have to do so as to update the image of the Alt-Tab, but even when restarting the process that handles the Alt-Tab (I suspect unity), apparently it won't work, as I restarted the whole PC and it didn't.
The only thing I did was to install Shutter and then the image updated automatically. I suspected that a completely new entry to the unity panel may caused it, but it didn't, I tried with other programs I hadn't installed and no results :/

Does anybody have a clue here :P ?

---

### Post by collisionystm on 2011-10-29
Change your icon scheme completely

---

### Post by hakermania on 2011-10-29
> **collisionystm said:**
> Change your icon scheme completely

Well, that's isn't actually what I want to achieve :) I want to achieve something else through this which I will post here if I manage to do it:D
I'd really like to know how to get the alt-tab task to re-load the image from the /usr/share/icons/ folder. I have no idea when or under what circumstances it checks for the image from this folder. Even after restart it's like reading the image from elsewhere:confused:

---

### Post by hakermania on 2011-10-29
I tried to change the icon theme and then set it back with the hope that it'll reload the image normally but it didn't...
My current icon-theme is ubuntu-mono-dark and I set it to gnome (which has a complete different "view" of the 'Show Desktop' icon and then back to ubuntu-mono-dark
```

gsettings set org.gnome.desktop.interface icon-theme gnome
gsettings set org.gnome.desktop.interface icon-theme ubuntu-mono-dark

```
Show desktop doesn't seem to update properly.... It is very confusing to have something altered and not to be recognized easily.... It's like everything's being hold in memory. But, even then, how can a whole restart not work...? And even if the image is being copied and then hidden for later use in the depths of the system, why so? The show desktop icon is available in so many different sizes and easily accessible...
Help :P

---

### Post by hakermania on 2011-10-31
bUmp

---

### Post by hakermania on 2011-11-01
Bum&#928;

---

### Post by hakermania on 2011-11-02
pmub

---

### Post by hakermania on 2011-11-04
bump guys!

---

### Post by hakermania on 2011-11-09
bimp
I need to find out when and why the Alt-Tab picture of the desktop gets updated!

---

