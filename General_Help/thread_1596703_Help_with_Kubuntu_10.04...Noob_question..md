---
title: "Help with Kubuntu 10.04...Noob question."
date: 2010-10-14
forum: General Help
---

### Post by Juggernuts on 2010-10-14
I have two questions--

When I used the plasma widget (I guess that's what it's called?) to search for backgrounds, I find ones I like then I click "Install". It says they're finished and i'm pretty sure they're saved because the button changes to "Uninstall" after I click it, but my problem is I can't find where they're being saved at! I've searched just about every folder I can see and I've came up with nothing. Kubuntu shows the wallpaper it comes installed with when I try to change it, but the downloaded ones are no where to be found. Where do I need to go to find them?

Also, How do I turn on the cube in 10.04? does it come stock with Kubuntu or do I need to install Compiz...A guide would be extremely appreciated (I can't seem to find out where/what to install for this).

P.S.-I've tried changing windows to "4" and enable cube animation under the options in kubuntu(I'm not running it right now so I can't say the exact location) but it just gives me 4 screens on a flat plane I can scoot around on. I'm guessing Compiz is the only way to get the true cube?


Thanks so much for the help! I'm loving it so far.

---

### Post by dabl on 2010-10-14
Systemsettings>Desktop Effects> "Enable" turns on compositing, if your hardware will support it -- see the Advanced tab there.  There is a "cube effect" which is not the real deal Compiz cube, but it works pretty well for spinning from one desktop to the next.  If you're new, I would advise holding off on installing compiz until you've got a good handle on the system as it is now.

KDE effects, and plasma widgets -- here's a good forum to get help with that stuff:

[http://www.kubuntuforums.net/index.php](http://www.kubuntuforums.net/index.php)

---

### Post by ankspo71 on 2010-10-14
Hi,
There is no need to install Compiz for you to have a cube (although that is still optional), because KDE does have a decent cube of its own. One nice thing about the cube in KDE is that it works when you have 2x2 desktops in the pager, not just the usual 1x4. I'm not sure why you are getting a flat plane for a cube, but I'll see if I can find out what could have happened and I report back to let you know.

For the wallpaper that you downloaded through the KDE wallpaper interface thing, you should be able to find the wallpaper at:
/home/yourname/.kde/share/wallpapers/
Notice that ".kde" is a hidden folder. 

Adding wallpapers in Kubuntu 10.10 has improved because it will automatically display the wallpapers found in /home/yourname/.kde/share/wallpapers/ too, not just /usr/share/wallpapers. 

Hope this helps.

---

### Post by ankspo71 on 2010-10-14
Hi again.
Is it possible that you might have enabled desktop grid, but not desktop cube or desktop cube animation? The default keyboard shortcut for the cube is Ctrl+F11. If you have the cube enabled, the cube should appear when pressing those keys.

---

### Post by Juggernuts on 2010-10-14
1. How do I check to see if my hardware will allow compositing, and if  it doesn't allow for it will compiz go around the issue or will it  still not work?

2. I remember turning on compositing but when I went back to it later it was in red with some kind of error (i'll take a screenshot later). I'm not sure if I had my settings correct. I know for a fact I had the cube animation enabled as well as compositing. I then went to number of desktops and set it to 4 but i'm not sure if I was supposed to do that or not...

3.How do I show hidden files so I can find my screensavers? 

My specs are 
8 gigs corsair ram
AMD Phenom II quad core
ATI HD4650 (not 100% sure on my video card, i'll have to verify when I get home)


Sorry for the barrage of questions, and thanks again for the quick responses!

---

### Post by Juggernuts on 2010-10-14
Just saw your post, i'll also try using the keyboard combo but i'm almost 100% positive I had cube animation enabled. When I selected "4 desktops" it turned my screen into a plane where I could scroll between desktops when I clicked and dragged.

---

### Post by ankspo71 on 2010-10-14
If it doesn't work out with Kwin's desktop cube, here is my way to install Compiz and Emerald in Kubuntu. Sorry in advance about this mini howto looking a little rough. I am testing this out as I write it in Kubuntu 10.10.

To install compiz, open a terminal and paste this command into it:
```
sudo apt-get install xutils compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-settings-manager fusion-icon emerald
```

This will install Compiz with KDE support and extra plugins, the Compiz Configuration Settings Manager, Fusion Icon to run in the system tray (it may be needed to enable/control compiz), and the Emerald Theme Manager (for window borders that are more compiz compatible). These packages should be available in Kubuntu 10.04 too.

Next disable Desktop Effects in KDE.

Now enable "KDE compatibly" plugin in the Compiz Configuration Settings Manager. Then close the manager before making more changes.

Choose Compiz to be the default window manager in KDE. In KDE 4.5+ the location is:
System Settings > Default Applications > Window Manager > "Use a different window manager": = Compiz

In KDE 4.4 the location might be:
System Settings > advanced tab > Default Applications > Window Manager > Window Manager again? > "Use a different window manager": = Compiz

The above step will apply compiz for you for the first time.
but if it doesn't, run the command:
compiz --replace

Now use the command:
emerald --replace

Restart your computer.

That should do it. It is working well for me. Now you can go enable compiz cube and other desktop effects  in Compiz Configuration Settings Manager.

Possible problems:
Check to see if you have window borders and 3d effects. If not, you will need to make an autostart entry for "fusion-icon" (or "compiz --replace" and/or possibly "emerald --replace"). The KDE plasma widget called "Pager" is known not to like compiz very much, but it is working well for me right now.

More resources:
[http://kubuntuguide.org/Lucid#Compiz_Fusion](http://kubuntuguide.org/Lucid#Compiz_Fusion)
[http://www.kubuntu.org/doc/7.10/config-desktop/C/tips.html](http://www.kubuntu.org/doc/7.10/config-desktop/C/tips.html)

---

### Post by dabl on 2010-10-14
There's a 3-second test to determine whether you have compositing enabled.  Open a terminal window and run ```
glxgears
```

If you see gears, you have compositing.  No gears, no compositing.

:guitar:


p.s.  It is possible you'll have to install the mesa-utils package first.

---

### Post by Juggernuts on 2010-10-15
Thank you so much guys! Soon as I get off today ill try this out. Also, how do I find hidden folders?

---

### Post by ankspo71 on 2010-10-15
> **Juggernuts said:**
> Also, how do I find hidden folders?

When you open your home folder in Kubuntu with the default file manager (Dolphin), you can press left Alt plus Period (alt + .), or you can enable "Show Hidden Files" up there in the view menu. Any file or folder that begins with a period is a hidden file.

---

