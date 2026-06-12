---
title: "Change the default icons of folders (like on Karmic)"
date: 2010-01-03
forum: General Help
---

### Post by N00b-un-2 on 2010-01-03
specifically what I am trying to accomplish is to set the default icons of folders to be something other than the generic folder, much like the ones that are in the home directory on Karmic.

I do not mean right click and change the icon manually.  Let me give you an example of what I mean.

Lets take the music folder for example.  Keep in mind that I am running Hardy, not Karmic so the default *$HOME/Music* folder is a generic folder icon, even if I use the Humanity icon theme.  So there is a configuration file SOMEWHERE that tells the folder what icon to use.
Many other icon themes have specific icons for each folder in the home directory which use the same names for the custom folder icons as Humanity.  eg; the Music folders name would be 'folder-music'.  Try it!  Create a launcher on your desktop.  Then edit the icon (it is a .desktop file) with gedit and replace all the instances of *icon="something here"* with *"folder-music"*, instead of using the full path to the icon.  This way, when you change to another theme that supports this icon, it will change.
Other themes that do this include Mac4Lin, Hydroxygen, Mashup, Breathe, Maelia, etc...  

Why is there no easy way to change DEFAULT icons, so that they change when your icon theme changes?

---

### Post by warfacegod on 2010-01-04
I've used ubuntu to since 7.04. I've never had an icon not change when I change my icon theme.

---

### Post by N00b-un-2 on 2010-01-04
I don't think you are getting my point.  I want to set custom icons for folders in my home directory.  If I change them manually to '/usr/share/icons/some-theme/128x128/some-icon.png' then that folder is stuck with that icons even when I change icon themes.

but LOTS of icon themes have unused icons for your home folders, typically called *folder-documents, folder-music, etc.*.  I want to be able to change icon themes and have custom icons change to their corresponding icons in other themes. make sense?

---

### Post by warfacegod on 2010-01-04
Yeah, I'm not sure you can do what you want. How would the new theme know how to make the appropriate correlation? Unless it did it by image resolution 12X12 16X16 etc. I can't help you with his but can suggest you post this in the Desktop Environments section, your question seems like that would be a more appropriate place to find answers and/or help.

---

### Post by sandman3838 on 2010-01-04
I think you and I have been trying to solve the same issue?

Take a look at this:

[http://ubuntuforums.org/showthread.php?t=1319633](http://ubuntuforums.org/showthread.php?t=1319633)

---

### Post by poosterl on 2010-01-20
Did you finally figure out how to revert to the default icons? I have the same problem : my Music folder being stuck with an icon I manually configured.

---

