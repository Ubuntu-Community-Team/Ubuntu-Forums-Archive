---
title: "Different wallpapers on different workspaces in Ubuntu 10.04"
date: 2010-05-05
forum: General Help
---

### Post by pkchips on 2010-05-05
Hello,

The old methods of getting different wallpapers on each workspace do not seem to work anymore. I was wondering how this can be accomplished in 10.04?

---

### Post by f35acepilot on 2010-05-05
I'm looking for this too. I tried the wallpapoz solution, but it seemed very unstable, took a long time to switch backgrounds, and didn't work anymore after restarting my computer.

---

### Post by Vaphell on 2010-05-05
gnome doesn't have that feature, on the other hand kde reportedly has.

---

### Post by Lightstar on 2010-05-09
I've been looking for the same thing.
The Cube options do not have any cube sides/wallpapers, just caps.
I don't see the 'wallpaper' plugin.  Maybe it can be found separately and added to compiz.

---

### Post by sparklyprgs on 2010-05-16
> **Lightstar said:**
> I've been looking for the same thing.
The Cube options do not have any cube sides/wallpapers, just caps.
I don't see the 'wallpaper' plugin.  Maybe it can be found separately and added to compiz.

I've searched pretty extensively and can't find anyone that's been successful making this work under 10.04 Lucid. Only thing I can think of is to have a closer look at an older 9.10 system that's been setup with this feature find and see if there's a way around this. Not really sure where to look other than gonf-editor.

Another idea: Is there a way to get older versions of compizconfig-manager? Because we could try removing the latest version and installing the older one.

---

### Post by kannerke on 2010-05-17
Hi,

The wallpaper plugin is now located in 'compiz-fusion-plugins-extra'.
You can simply install it via the synaptic package manager.


best regards,
Peter

---

### Post by Letha on 2010-06-11
Hey Fellas,

I have been working with Ubuntu since about a year and I would like to share what I have done to be able to have different wallpapers on my workspace.

[http://ubuntuforums.org/showthread.php?t=17359](http://ubuntuforums.org/showthread.php?t=17359) -> Post from Member elgilicious

**I completed Step I & II** but I realized that *Step III seemed to be outdated on 10.04 *so I came across this thread and read kannerke's post,[B] 
aditionnaly installed 'compiz-fusion-plugins-extra' [/B]went to  [B]
System --> Preferences -->Compizconfig--> Tools--> Wallpapers[/B] 
chose my images and  "hoooray it works" 

There are two things that still don´t work as well as I expected.

1) The standard Ubuntu desktop pops up i the background when you start or shut down your binary buddy.
(I´d just choose a plain black background and it did not bother me any longer)

2) You won´t see any of your shortcuts anymore. 
(I use** Cairo as a Dock** so this one did not bother me either, I think its probably just a layer that needs to be set up right as my **Cairo Desklets & Starters do work like a charme**, but I may be wrong with my assumption) 
  
Finally I´d like to thank elgilicious & kannarke as I wouldn´t have multiple wallpapers without their documentation ):P !

Best regards Letha

---

### Post by AnThoMan on 2010-08-12
> **Letha said:**
> Hey Fellas,

**I completed Step I & II** but I realized that *Step III seemed to be outdated on 10.04 *so I came across this thread and read kannerke's post,[B] 
aditionnaly installed 'compiz-fusion-plugins-extra' [/B]went to  [B]
System --> Preferences -->Compizconfig--> Tools--> Wallpapers[/B] 
chose my images and  "hoooray it works" 



This step doesn't work for me :(

For some reason only the second (of five) workspaces shows the designated wallpaper using this method, the remaining four all show white backgrounds. 

Any ideas?


Much appreciated,

Andrew

---

### Post by AnThoMan on 2010-08-13
> **AnThoMan said:**
> This step doesn't work for me :(

For some reason only the second (of five) workspaces shows the designated wallpaper using this method, the remaining four all show white backgrounds. 

Any ideas?


Much appreciated,

Andrew

Have played around a bit more and found that only certain images will display..

Are there any parameters (pixels, ratios, file name etc) that are required for this to work?

---

### Post by Halfling Rogue on 2010-12-04
Doesn't work for me either. Installed the Compiz extras and the Wallpaper option seems to be accepting images fine, but unticking the Nautilus show-desktop just makes the icons disappear - the GNOME desktop stays in place. Going to desktop -> background in the gconf has draw_background, but if I uncheck that I just get the GNOME bg colour all over my workspaces. Setting the picture_opacity does absolutely nothing with any settings (which is a shame, because if it did it could probably be used with a 0 setting to fix this).

Anybody else got any ideas?

---

### Post by JeanVW14 on 2010-12-13
+1

Why has 10.10 broken all my nice eyecandy. Impulse too.

Anyone managed to fix this yet?

---

### Post by wolke on 2011-01-01
does this fix for you folks?

its a workaround from:
[http://forum.ubuntu-fr.org/viewtopic.php?id=421649](http://forum.ubuntu-fr.org/viewtopic.php?id=421649)

the attachment is the file i got from here:
[http://www.mediafire.com/?usji79x5yiu5d3z](http://www.mediafire.com/?usji79x5yiu5d3z)  ( wallpaper plugin - 64bit module - File Size: 96.69KB )

backup and then replace:
/usr/lib/compiz/libwallpaper.a
/usr/lib/compiz/libwallpaper.la
/usr/lib/compiz/libwallpaper.so

with the ones in the file attached

---

### Post by emmiesix on 2011-06-21
Thank you!!  Replacing those files fixed the final annoyance of 11.04.  What a terrible idea to upgrade...

---

### Post by pqwoerituytrueiwoq on 2011-06-21
i got it on 10.04

terminal:
```
gconftool-2 --type bool --set /desktop/gnome/background/draw_background false
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```
now compiz wallpaper can take over
but you loose desktop icons and desktop context menu

undo:
```
gconftool-2 --type bool --set /desktop/gnome/background/draw_background true
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true
```
you may want to un-check the wallpaper addon in compiz to regain some ram

---

