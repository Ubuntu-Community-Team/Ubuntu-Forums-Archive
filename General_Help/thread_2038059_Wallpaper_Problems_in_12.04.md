---
title: "Wallpaper Problems in 12.04"
date: 2012-08-05
forum: General Help
---

### Post by clegends on 2012-08-05
Hey folks, I've stuffed up my wallpapers, and need some help sorting out permissions again. Firstly, not into grapical solutions, I prefer the commandline, particularly when dealing with permissions. Secondly, I've used Linux for years, and don't need to be told I shouldn't be messing with permissions as root. What I would really appreciate is getting back my wallpaper settings to something resembling a clean install. 

I was having problems with my login screen in 12.04 not reflecting my desktop wallpaper... just stayed with the stock purple. Read up and found out that this was because I had encrypted by home folder on install. Irritating bug, but makes sense. Up until then, everything was working perfectly. The solution of course was to add the image I wanted to use for wallpaper to the /usr/share/backgrounds folder, then navigate to it from the wallpaper chooser gui. Worked great. Unfortunately, in the process I stuffed just about everything up with permissions, standard wallpapers, etc. Now I have a collection of non-stock wallpapers, and the login screen for my guest user is black with white dots. Login for my actual desktop is fine, and reflects my current wallpaper.

I have another install of 12.04 on my wife's netbook, and intend to drop all the wallpapers from the default install back into the /usr/share/backgrounds folder. Seemingly though, unless I set the permissions to chmod 777, my desktop user can't actually see them in the gui...

So after I return the wallpapers to their rightful place, what permissions do I need to set for them? I like to use my install to show off to friends, so would like it all working properly. Oh, I also don't have ANY wallpapers to choose from now in the GUI, even though they exist in the folder... wondering if there's a database somewhere that's reading them.

Appreciate any thoughts you might have to help me sort this out. Thanks!

---

