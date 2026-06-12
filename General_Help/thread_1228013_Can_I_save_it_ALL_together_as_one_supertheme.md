---
title: "Can I save it ALL together as one supertheme?"
date: 2009-07-31
forum: General Help
---

### Post by DGeeez on 2009-07-31
I've had a lot of fun playing with themes for window borders, icons, controls, wallpaper, mouse pointers, and sounds, thanks  to those who've helped me find it all. I particularly love the way you can install icons, controls, and window styles as one theme, and then use the individual tools for customizing your own. But I'm frustrated that the wallpaper I select won't save as part of the any new theme package which I try to create, and switching my saved themes (whether custom or downloaded) never changes the wallpaper. Because feedback for a cursor theme change requires a reboot, I don't know yet whether a selection in that department would get saved as part of a custom theme which I've saved called "The Evil Gnome", but ideally, it's not just the dark window backgrounds, borders, and icons, but the wallpaper with glowing footprint and lightning, sparking cursor, and system sounds, too! I can set all of these individually, but the settings are not saved as the one super-theme which I would want, so that all this can be done in one move. Does anyone have a way of doing that?

Thanks.

---

### Post by CatKiller on 2009-07-31
In your metatheme (the file that ties all the bits together, that is usually called index.theme) you can specify a background image and a cursor theme with the cryptically named BackgroundImage and CursorTheme elements. I'm not sure about sounds, since I've never played with them.

---

### Post by DGeeez on 2009-07-31
> **CatKiller said:**
> In your metatheme (the file that ties all the bits together, that is usually called index.theme) you can specify a background image and a cursor theme with the cryptically named BackgroundImage and CursorTheme elements. I'm not sure about sounds, since I've never played with them.

Metatheme - that's the ticket, thanks! So, is there a way to save separate metatheme files, or would I need to save different versions of index.theme under appropriate names, and then rename one of those files when I want to apply it?

---

### Post by CatKiller on 2009-07-31
> **DGeeez said:**
> Metatheme - that's the ticket, thanks! So, is there a way to save separate metatheme files, or would I need to save different versions of index.theme under appropriate names, and then rename one of those files when I want to apply it?

When you select a theme from the Appearance tool, and you see the list of themes that contain all of the icons, window decorations and GTK+ widgets, that's because of the metatheme that ties them together. If you customise a theme, you get to select each of the types of theme individually, and you'll probably find that there are more icon themes, say, than you've got metathemes. Depending on where you got it from, you may also get a prompt that a particular theme suggests a background image which you can choose to apply or not. The group of French themes that are popular at the moment work like this, which is how I now how it works.

This is what you'll be re-creating when you make your own custom theme. You'll make a folder called the name of your theme in that will contain your Metacity and GTK+ themes, in ~/.themes, and make a folder in ~/.icons with your icon theme in. In the sub-folder of ~/.themes will be the index.theme file. All of this will probably be done for you if you select Save Custom (or whatever the option is called in the Appearance tool). Then you just need to tweak the index.theme so that it refers to your chosen background and cursor theme too. The GTK+/Metacity/icon themes don't necessarily have to have the same names; they are referred to individually by name in the index.theme file.

If you want a different combination of background/cursor/GTK+/Metacity/Icon themes to be similarly easily selectable, you'd save that combination as a different theme with a different name. Tweak to taste.

I did notice, when I was looking at an index.theme file before my earlier post, that you can also specify the Application font to go with a particular theme. I don't know if this is the kind of customisation that you've done already, but it might be useful information, and so I pass it on.

The format of the index.theme file is really straightforward. I suggest you poke around at some, either in ~/.themes or in /usr/share/themes. Once you've got your metathemes to do what you want, you only need to select them in the Appearance tool for all the pieces to automagically change. No manual renaming needed.

---

### Post by DGeeez on 2009-07-31
> **CatKiller said:**
> When you select a theme from the Appearance tool, and you see the list of themes that contain all of the icons, window decorations and GTK+ widgets, that's because of the metatheme that ties them together. If you customise a theme, you get to select each of the types of theme individually, and you'll probably find that there are more icon themes, say, than you've got metathemes. Depending on where you got it from, you may also get a prompt that a particular theme suggests a background image which you can choose to apply or not. The group of French themes that are popular at the moment work like this, which is how I now how it works.

This is what you'll be re-creating when you make your own custom theme. You'll make a folder called the name of your theme in that will contain your Metacity and GTK+ themes, in ~/.themes, and make a folder in ~/.icons with your icon theme in. In the sub-folder of ~/.themes will be the index.theme file. All of this will probably be done for you if you select Save Custom (or whatever the option is called in the Appearance tool). Then you just need to tweak the index.theme so that it refers to your chosen background and cursor theme too. The GTK+/Metacity/icon themes don't necessarily have to have the same names; they are referred to individually by name in the index.theme file.

If you want a different combination of background/cursor/GTK+/Metacity/Icon themes to be similarly easily selectable, you'd save that combination as a different theme with a different name. Tweak to taste.

I did notice, when I was looking at an index.theme file before my earlier post, that you can also specify the Application font to go with a particular theme. I don't know if this is the kind of customisation that you've done already, but it might be useful information, and so I pass it on.

The format of the index.theme file is really straightforward. I suggest you poke around at some, either in ~/.themes or in /usr/share/themes. Once you've got your metathemes to do what you want, you only need to select them in the Appearance tool for all the pieces to automagically change. No manual renaming needed.

This may be getting to be too far beyond my understanding to deal with just yet, but I'm hoping you might understand my search results, which I'd like to make sense of before I give this up.

I did a Terminal session Locate command (Nautilus would make a bit more sense if it would display the paths, especially for each of your search results) for all index.theme files from the root, and noticed that some of the themes which I had downloaded and installed the day before were displayed - but certainly not all of them, not even close! Well, maybe those which display are what the Metacity wiki folders refers to as "theme engines", (I had no idea on all these components behind the GUI), but if I need to look within one of these indexes to find the specs for engine-based themes I download or derived and saved, I'm not really sure which of them it is.  I was hoping to find actual files or folders for the custom themes which I had saved, but none displayed. I could not find any from a root search with the names which I had saved themes (in some kind of form) with in the Appearances->Themes box, which are still showing there! Here's the Terminal output, which does not contain any which I had derived and saved from Ubuntu-Look themes like Blue-joy, Grey_Human, Industrial, which are displayed in the Appearances->Customize->Controls windows along with some which are included on this list:
```
mrg@mrg-desktop:/$ locate index.theme
/home/mrg/.themes/ColorBit/index.theme
/home/mrg/.themes/Orange-LiNstaBlackPlastic/index.theme
/home/mrg/Themes/Darker theme/index.theme
/home/mrg/Themes/Darker theme/index.theme~
/usr/share/icons/Crux/index.theme
/usr/share/icons/DMZ-Black/index.theme
/usr/share/icons/DMZ-White/index.theme
/usr/share/icons/HighContrastInverse/index.theme
/usr/share/icons/HighContrastLargePrintInverse/index.theme
/usr/share/icons/Human/index.theme
/usr/share/icons/Mist/index.theme
/usr/share/icons/Tangerine/index.theme
/usr/share/icons/crystalsvg/index.theme
/usr/share/icons/default/index.theme
/usr/share/icons/gnome/index.theme
/usr/share/icons/hicolor/index.theme
/usr/share/icons/nimbus/index.theme
/usr/share/icons/oxygen/index.theme
/usr/share/sounds/ubuntu/index.theme
/usr/share/themes/Clearlooks/index.theme
/usr/share/themes/Crux/index.theme
/usr/share/themes/Dust/index.theme
/usr/share/themes/Dust Sand/index.theme
/usr/share/themes/Glider/index.theme
/usr/share/themes/Glossy/index.theme
/usr/share/themes/HighContrastInverse/index.theme
/usr/share/themes/HighContrastLargePrintInverse/index.theme
/usr/share/themes/Mist/index.theme
/usr/share/themes/New Wave/index.theme
/usr/share/themes/dark-nimbus/index.theme
/usr/share/themes/light-nimbus/index.theme
/usr/share/themes/nimbus/dark-index.theme
/usr/share/themes/nimbus/index.theme
/usr/share/themes/nimbus/light-index.theme


```

---

### Post by CatKiller on 2009-08-01
> **DGeeez said:**
> Here's the Terminal output, which does not contain any which I had derived and saved from Ubuntu-Look themes like Blue-joy, Grey_Human, Industrial, which are displayed in the Appearances->Customize->Controls windows along with some which are included on this list:

The themes that are listed in the Controls section are GTK+ themes. I said before that you'll have individual components that aren't shown in the main window, since you'll only get them show up in the main window if they've been selected in some combination.

Actually, I just checked, and you can do it all from the Appearance tool. If you've already got your Custom theme set up how you want, select Save As... and put in the name you want to call it. Tick "Save background image" if you want to save the background image along with the theme. If you sill want to find the index.theme file for the metatheme you just created, it will be in ~/.themes/<whatever you called your theme>/

---

### Post by DGeeez on 2009-08-01
> **CatKiller said:**
> The themes that are listed in the Controls section are GTK+ themes. I said before that you'll have individual components that aren't shown in the main window, since you'll only get them show up in the main window if they've been selected in some combination.

Actually, I just checked, and you can do it all from the Appearance tool. If you've already got your Custom theme set up how you want, select Save As... and put in the name you want to call it. Tick "Save background image" if you want to save the background image along with the theme. If you sill want to find the index.theme file for the metatheme you just created, it will be in ~/.themes/<whatever you called your theme>/

I found the Save Background button (thanks), which if used will cause a "suggested" bar to appear when you apply it. I find this to be something like being asked if you want your tires installed with air in them, and then there's at least one theme where that "suggestion" fails to appear when I apply it, even though I saved the wallpaper with it. Oh, well.

Anyway, I've got all the visuals tied in together, if not the startup sounds, too. 

Another thing which I would really like to do, being that so many icon theme options make it ever more difficult to find one which is perfect for you, is to edit those themes. Of course,these icon themes all have names which appear where you select them in Systems->Appearances->Custom, but a root search in Nautilus does not produce any files of like names other than the tarball which I had downloaded, before dragging it to the Appearances window. Not sure I understand how tarballs differ from zip files, and then I'm kinda impressed how modern zip/archiveware lets you preview files in some kinda temp folder before you unpack them. It just doesn't seem right that the tarball contents were never permanently written in any human-viewable/editable form. It's as if the file were directly absorbed by the system somehow. If I could find and access the folder containing a specific icon theme with the text command files which control them, then I'm sure I could figure out how to change them to my liking, IF it's the folder which is actually accessed by the GUI system. Do you know anything about doing this?

---

### Post by CatKiller on 2009-08-01
Per-user icon themes (such as when you drag-and-drop an archive to the Appearance tool) are kept in ~/.icons. System-wide icon themes are kept in /usr/share/icons.

The **locate** command does a lookup of a database to find files. If this database isn't updated, it won't show newly-created files. This database is updated on a reboot (IIRC) or if you run the command ```
sudo updatedb
```

---

### Post by DGeeez on 2009-08-01
> **CatKiller said:**
> Per-user icon themes (such as when you drag-and-drop an archive to the Appearance tool) are kept in ~/.icons. System-wide icon themes are kept in /usr/share/icons.

The **locate** command does a lookup of a database to find files. If this database isn't updated, it won't show newly-created files. This database is updated on a reboot (IIRC) or if you run the command ```
sudo updatedb
```

Thanks! At least I know there somewhere, now.

Sorry that I have to keep coming back with so many questions, but I wondered first why Nautilus refuses to open index.theme files with the error "it's a directory" (don't know how it doesn't look like a file). When Terminal complied and opened the same index.theme (which seems to be the only folder non-icon file in the oxygen directory), I saw some strange characters mixed in, strings with lines through them, and no icons names referenced! Where is the file then where you assign icons for specific user options?

---

### Post by CatKiller on 2009-08-01
> **DGeeez said:**
> I wondered first why Nautilus refuses to open index.theme files with the error "it's a directory" (don't know how it doesn't look like a file). 

Yeah, Nautilus handles some text file types in a peculiar way. It won't open .desktop files either. You can still drag-and-drop to a text editor though. I normally just use **less** for viewing or **nano** for editing on the command line. That's probably because I have a handy launcher for the command line and not for Gedit, though.

Icon themes are different to the meta-themes we discussed earlier. I'm not entirely sure what the index.theme for icon themes does, other than simply state which classes of icons are available. Icon themes work simply by having the correctly-named file in the appropriate place for a given function at a given size. What each file is for is outlined in general in the freedesktop.org link I believe I gave you in the other thread.

Actually, I've just remembered an important function of the index.theme for icon themes; it contains the Inherits= line, which tells it which icon themes to use, in which order, to fill in any blanks that aren't included in that theme. For example, Tropical (which I'm using now) has no system-log-out file included, so the Inherits= line tells it to next check NuoveXT2 (which I don't have) and then Human (which I do). The icon for the Log Out option on the main menu is therefore the default Human one.

---

### Post by DGeeez on 2009-08-02
Thanks, CatKiller! I found the folders you referred me to, including the hidden one! 

My system looks great as it is, but I just wanted to change an icon or two in an iconset which I otherwise liked, and had no idea how complex these things are. I expected to see function to icon association links somewhere, and what I see on my system reveals that an iconset tree contains the same icons again for each size, and within each size set is it's own set of folders for function categories (one of them handles the application icons on my GNOME bar). The icons within cross-link each other dozens of times, if not more, and I don't see anything within these folders other than the icon names which link them to actual programs, menus, whatever, so the short of it is that what I am trying to do is nothing so straightforward as what I am used to, like changing my system startup sound. So, when I can manage it, I'll be off to freedesktop.org as you said, to become an expert.

Thanks again.

---

### Post by CatKiller on 2009-08-02
The symbolic links are there just to save on disk space; if you want to have the same file lots of times without actually having the file lots of times, you use a symbolic link. They're very useful.

The different sizes thing can get a bit tedious, but the idea is that an icon that looks great at 48x48 probably needs to be simplified before it will be clear what it is at 16x16. It's a user interface guideline thing. This structure means that you can hand-tune the icons so that they'll be good at whatever size they're used. Scalable (SVG) icons can be used at any size, but if an equivalent icon can been used at the specified size, that will be used instead. There are more guidelines [here]("http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines") and [here]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes").

The easiest way that I've found to identify which file gets used for which thing is to find a theme that has an icon for what I'm interested in (the Tango theme is pretty complete) and find the file in there. Then I'll create (copy/symlink) an equivalent file in the theme that I want to use.

---

