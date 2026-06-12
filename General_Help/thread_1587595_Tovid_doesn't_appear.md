---
title: "Tovid doesn't appear"
date: 2010-10-03
forum: General Help
---

### Post by FinalShot on 2010-10-03
I installed tovid, it isn't under Apps -> S & V -> tovid. I refreshed the panels with:

```
killall gnome-panel
```

I read some posts about dependencies, what are they ( so I can install them, if any )?

Any help would be appreciated.

---

### Post by andrewthomas on 2010-10-03
try to log out and back in.  If that doesn't work look in system > preferences > main menu.

---

### Post by FinalShot on 2010-10-03
Restared to be sure, nothing appeared. Checked S & V under main menu preferences, it wasn't there either.

---

### Post by andrewthomas on 2010-10-03
```
 
sudo apt-get install tovidgui

```
 
How about that?

---

### Post by oldos2er on 2010-10-03
tovid is a CLI app, hence no menu entry.

---

### Post by FinalShot on 2010-10-04
According to [this]("http://ubuntuforums.org/showthread.php?t=183936") topic, it does, oh well.

Are these all the possible command line options?

```
    -dvd | -half-dvd | -dvd-vcd         Encode to standard DVD format
    -vcd | -svcd                        Encode to (S)VCD format
    -kvcd | -kvcdx3 | -kdvd | -bdvd     Encode to non-standard MPEG-2 format
    -pal | -ntsc | -ntscfilm            Set TV standard

```If not, a complete list would be nice. If there are any similar programs that have a GUI, that would be better, as I'm looking for customization, not usability ( Pretty much looking for a DVDFlick alternative ).

**Edit:** Just seen your post Andrew, trying it now.

---

### Post by FinalShot on 2010-10-04
The tovid GUI is great, but it fails every time about untitled_xx.mpg file missing.

---

