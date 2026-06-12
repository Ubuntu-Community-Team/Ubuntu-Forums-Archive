---
title: "Ambitious desktop configuration"
date: 2011-10-11
forum: General Help
---

### Post by KebertX on 2011-10-11
I'm relatively new to 11.04, and I'm still undergoing the desktop customization process. Feel free to let me know if this isn't doable, but I have a feeling there's a way.

I set my desktop wallpaper to an XML slideshow. I installed compiz-config and set my workspace settings to 'Desktop Cube.' All the tutorials say that should allow me to have a different wallpaper on each desktop. I don't see what I'm supposed to at this point:

[IMG]http://anuragbansal.files.wordpress.com/2008/05/appearance.png[/IMG]
^From the guide I'm looking at^
Under appearance, I see an option for "Skydome" (Possibly analogous to "Cube Caps," this is for an earlier edition of ubuntu), but what I do not see is anything for me to include multiple background images. I digress...

Here's my real issue, can I use a different XML slideshow on each of my workspaces? Let me skip the issue of impoting multiple images on the compiz-config cube settings. I get the sense that this would be easy if I were able to right click on my desktop. That seems to be the price of fancy cube-switchery, but I don't want to compromise that, it's too damn important!

tl;dr different Desktop Background slideshows on each of my workspaces. Can it be done?

---

### Post by hwttdz on 2011-10-12
In general the solution recommended involves disabling the desktop drawing by nautilus and using the compiz wallpaper.  I'm not fond of this solution because it involves sacrificing desktop icons.  

One possibility would be using a command similar to
```
gconftool --type string --set /desktop/gnome/background/picture_filename "/path/to/your/image.png"
```
every time the workspace is switched.  And one could check for workspace switching via:
```
wmctrl -d
```
and a little parsing of output.  

The tricky bit would be getting the script to run on workspace switches.  If you use the keyboard shortcuts then you could use something like autokey to first run the script and then pass the keys to switch the workspace, if you use the mouse I'm out of ideas at the moment.  If I knew how gnome switched workspaces we could just hack that command.

A super ugly solution would be to just put the script in an infinite loop that was perpetually watching for desktop changes.

---

### Post by hwttdz on 2011-10-12
I drafted the quick and dirty solution, you can find it [here]("http://astoryworthtelling.wordpress.com/2011/10/12/one-wallpaperbackground-per-desktopworkspace-in-ubuntu-with-icons/").

You have to update a couple of paths to use it and put your files in 1.ext, 2.ext, 3.ext... and so on (one per workspace).  And if you're using xml you have to change the extension to xml.  But it shouldn't be too much issue to setup.

---

### Post by KebertX on 2011-10-23
> **hwttdz said:**
> I drafted the quick and dirty solution, you can find it [here]("http://astoryworthtelling.wordpress.com/2011/10/12/one-wallpaperbackground-per-desktopworkspace-in-ubuntu-with-icons/").

You have to update a couple of paths to use it and put your files in 1.ext, 2.ext, 3.ext... and so on (one per workspace).  And if you're using xml you have to change the extension to xml.  But it shouldn't be too much issue to setup.

You sir, are neat. Thank you for your stupendous neatness. *

---

