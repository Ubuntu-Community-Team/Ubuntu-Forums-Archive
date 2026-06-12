---
title: "wallpapers and appearances"
date: 2009-08-02
forum: General Help
---

### Post by sidewalkcynic on 2009-08-02
I found a wallpaper app in synaptic, 'wallpaper tray,' that changes the wallpaper at specified intervals, but I screwed up backgrounds trying to get it to designate a directory.The app wouldn't seem to take to any directory I gave it.

I mistakenly designated /usr/share/gnome-background properties, looking for /usr/share/background, and it flickered and didn't do anything; and so I rebooted. When starting up the desktop flickers a window, that looks like a Nautilus browser window with no words or icons. I cannot adjust system> preferences> appearence - the window opens for a half second then closes. My Gnome sticky notes does not stay open when selecting a new note. I cannot control the wallpaper/background all, and it uses the custom splash as a desktop background.:confused:


So, I removed the wallpaper tray app in synaptic, but still have problems.

Here is a copy of the ubuntu-wallpapers.xml file that I must have hooked up to to with the wallpaper tray app that caused the problem
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper>
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#8f4a1c</pcolor>
    <scolor>#8f4a1c</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/heron-simple.png</filename>
    <options>zoom</options>
    <pcolor>#8f4a1c</pcolor>
    <scolor>#8f4a1c</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>Elephant</name>
    <filename>/usr/share/backgrounds/simple-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#dab082</pcolor>
    <scolor>#dab082</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
</wallpapers>
```

---

