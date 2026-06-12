---
title: "Cursor Trouble"
date: 2011-01-19
forum: General Help
---

### Post by Spirrwell on 2011-01-19
I'm using Ubuntu 10.10 64 bit edition. I've tried to install two different sets of cursors now, and neither have worked. The cursors PARTIALLY work, when you login it shows up the cursor for one second and goes back to the default DMZ-White cursor set. Also, if I'm in a certain application like VirtualBox, the cursors completely work, but once the cursor moves outside of the window it goes back to the default DMZ-White. I skimmed through the forums, I didn't see anything like this, I'll look a bit harder, but is there a way to fix this?

I installed the theme like this:
```

sudo cp -r ~/Desktop/Ecliz /usr/share/icons
sudo nano /usr/share/icons/default/index.theme

```
What am I doing wrong?
(Yes I edited the index.theme appropriately)

---

### Post by Spirrwell on 2011-01-19
bump

---

### Post by Spirrwell on 2011-01-19
Bump... any help?

---

### Post by Spirrwell on 2011-01-19
Bump... any help?

---

### Post by Spirrwell on 2011-01-19
Edit: Multiple posts.

---

### Post by Spirrwell on 2011-01-19
Edit: Multiple posts

---

### Post by VCoolio on 2011-01-19
The settings in index.theme are overwritten by your user configuration or gnome-settings-daemon. Set your cursor theme using system > preferences > appearance > customize > mouse cursor and see what happens. Or if you don't have gnome-settings-daemon running add a line in ~/.gtkrc-2.0 like:
gtk-cursor-theme-name="Ecliz"
Or set it in ~/.Xdefaults with a line like: 
Xcursor.theme: Ecliz
Remember the theme name is picky on caps, make it exactly as it looks like in the theme's index file.

---

### Post by Spirrwell on 2011-01-19
Uh, none of the things you suggested exist. I did make sure that hidden files were viewable, but I don't see cursor settings, .Xdefaults, or .gtkrc-2.0.

Is there anything else, or something I need to install?

---

### Post by VCoolio on 2011-01-19
You can create those files in your home folder if they don't exist yet; then logout and back in.

---

### Post by Spirrwell on 2011-01-19
"There is no application installed for X11 cursor files." is what I get for .Xdefaults, nothing happens for the .gtkrc-2.0 file. So there's something I have to install?

---

### Post by VCoolio on 2011-01-19
I don't know, is the theme ok? And there must be a 'pointer' tab in the appearance settings window, where you set the gtk theme and icon theme etc., click customize there.

---

### Post by Spirrwell on 2011-01-19
Yeah I just realized that, I didn't know you had to go into customize, I hate being new to things, especially operating systems, when you ask questions at first you sound like an idiot. Anyway, thanks.

---

