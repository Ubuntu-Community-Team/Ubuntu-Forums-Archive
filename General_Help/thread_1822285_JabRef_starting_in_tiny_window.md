---
title: "JabRef starting in tiny window"
date: 2011-08-10
forum: General Help
---

### Post by JohnMcL on 2011-08-10
I installed jabref via packages on lucid.

When I start it via command line or applications menu it starts, but is initially a minimal size (not minimized) window at the top-left of the screen.
If I resize or maximize it everything works properly.

This doesn't happen with other programs.

Any idea how I can get it to start in a normal usable size?

I tried resizing, closing, and reopening it.
I also tried having a database open or not.

---

### Post by somebodyelsehere on 2011-08-25
I have the same problem. I am running JabRef (2.4.2) under GNOME (2.30.2).

On my installation, there is a file ~/.java/.userPrefs/net/sf/jabref/prefs.xml which contains some entries with keys like "sizeX", "sizeY", "posX", "posY", "rememberWindowLocation" and many others. If I delete this file (move it to prefs.xml_old or something... otherwise you might permanently loose lots of configuration info!) and then start JabRef, the window starts with a usable / normal size, and the file prefs.xml is created with just a few lines of default values. I have tried deleting or changing the values of just some of the entries in prefs.xml, but so far have had no luck in getting just the window size to usable / normal without loosing other configuration info.

Maybe someone else has had more success?

---

### Post by somebodyelsehere on 2011-08-25
Found a solution for my setup. In ~/.java/.userPrefs/net/sf/jabref/prefs.xml I removed three lines, namely the ones for the entries "sizeX", "sizeY" and "rememberWindowLocation". You can do this using any text editor or even sed:

```

OLD_PREFS=~/.java/.userPrefs/net/sf/jabref/prefs.xml
NEW_PREFS=/tmp/prefs.xml
sed '/sizeX\|sizeY\|rememberWindowLocation/d' $OLD_PREFS > $NEW_PREFS

```maybe check to be sure you haven't deleted some other entries matching that expression...

```

diff $OLD_PREFS $NEW_PREFS

```and if it looks good (only the three entries we want to change appear in the diff output), move / replace the old prefs.xml with the modified prefs.xml

```

mv $NEW_PREFS $OLD_PREFS

```Then start JabRef again. The sizeX and sizeZ entries will be replaced with default values, but the rememberWindowLocation entry will not appear again by itself.

Still have no idea why / where the "wrong" window size is coming from (GNOME or xorg resources...?), but maybe this workaround is helpful for someone.

---

### Post by JohnMcL on 2011-08-26
Thank you, that was the problem.

I tried it first using webstart, maybe that is where the entries came from.

---

