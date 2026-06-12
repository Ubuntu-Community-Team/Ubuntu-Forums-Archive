---
title: "Change icon in Unity launcher (11.10)"
date: 2011-11-17
forum: General Help
---

### Post by edm1 on 2011-11-17
Hi all,

I just installed Freemind (which, on a side note, i think is an extremely useful program) but it has a really ugly icon in the unity launcher. So i set about changing the icon but cannot work out why it is not working.

So downloaded a nice new freemind icon to ~/Pictures/Icons/FreeMind_icon.png

Then i copied the .desktop file to my home folder 
```
sudo cp /usr/share/applications/freemind.desktop ~/.local/share/applications

```

Open the local .desktop file with gedit
```
gedit ~/.local/share/applications/freemind.desktop
```

and changed the icon line to
```
Icon=~/Pictures/Icons/FreeMind_icon.png
```

However, when i restart Unity I get an even uglier grey square box with a question mark in it.

Can someone help? Thanks.

---

### Post by MG&amp;TL on 2011-11-17
```
~/
```

Doesn't work. Use /home/<your name> instead.

Although I think you would be better changing an icon in /usr/share/icons/hicolor or /usr/share/pixmaps.

---

### Post by edm1 on 2011-11-17
Ah thanks. I thought there could be an easier way. If i open the icon in one of those folders using 'sudo gimp' and slot in my new icon, should that be all?

---

### Post by MG&amp;TL on 2011-11-17
This should work:

```
sudo cp -f ~/Pictures/mynewfabbypic.png /usr/share/pixmaps/theoldrubbishone.png
```

I'll just test.

EDIT: Yup, does work.

---

### Post by edm1 on 2011-11-17
i used the gimp method as i was going from png to xpm format, but thanks for the info. Solved.

---

