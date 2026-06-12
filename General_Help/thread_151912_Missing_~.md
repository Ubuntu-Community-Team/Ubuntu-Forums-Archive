---
title: "Missing: ~"
date: 2006-03-28
forum: General Help
---

### Post by Kaneda on 2006-03-28
I'm new to Linux and Ubuntu, and so I was reading a tutorial on the basics of the unix shell.  Well, I got to the point where it talks about using the tilde ~, and I tried to type it in, but for some reason my tilde won't work! I just get ` whether I push shift or not.  I'm pretty sure it is not a problem with my keyboard because my tilde works just fine in Windows.  Any help would be appreciated!

Thanks!

edit: by the way, I used copy and paste for the tildes I used in this post.

---

### Post by trent dillman on 2006-03-28
Check your xorg.conf and see what keymap you're using.

Here's what mine looks like:

```

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

```

You shouldn't change Identifier, and yours might be slightly different...

---

### Post by Kaneda on 2006-03-28
Here's what mine says:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"

```

Looks like it's about the same as yours...

---

### Post by Kaneda on 2006-03-28
bump

---

### Post by chocolatetoothpaste on 2006-03-29
dumb question, but did you try both shift keys?  For a long shot, rebooting?

---

### Post by Kaneda on 2006-03-29
[QUOTE=chocolatetoothpaste]dumb question, but did you try both shift keys?  For a long shot, rebooting?[/QUOTE]
yes and yes. still doesn't work.

---

### Post by Kaneda on 2006-03-29
Has anyone else had this problem before?

---

### Post by krusbjorn on 2006-03-29
I have no idea about other keyboards, but on my keyboard layout (swedish), it's AltGR, not shift.

---

### Post by Ramses de Norre on 2006-03-29
Is the tilde represented on the keyboard?
Does it work in other programs but the shell?
I can press the Page Down button in a shell and it gives a ~ then.

---

### Post by Kaneda on 2006-03-29
[QUOTE=Ramses de Norre]Is the tilde represented on the keyboard?
Does it work in other programs but the shell?
I can press the Page Down button in a shell and it gives a ~ then.[/QUOTE]
The tilde is represented on the keyboard, and it doesn't work in any programs at all.
However, pressing Page Down in the shell worked, but it doesn't work in other programs...

---

### Post by Kaneda on 2006-03-29
So nobody knows what's going on?

---

### Post by jeremiebergeron on 2006-03-29
Do you have any other keyboards around to see if they work? Also, does it work in any other operating systems (i.e. Windows)?

---

### Post by Kaneda on 2006-03-29
Nah, don't have any other keyboards, and this is my laptop keyboard.  Tilde works just fine in Windows...  Any ideas?

---

### Post by Barrakketh on 2006-03-29
The last time I checked laptop keyboards don't have 104 (or even 101) keys.  What model is your laptop?

---

### Post by Kaneda on 2006-03-29
It's an HP Pavilion dv1170us.  And there definitely is a tilde key on there to the left of 1, but whether I push shift or not, I always get `

---

### Post by Barrakketh on 2006-03-30
You could try another keyboard layout in GNOME...It's in System -> Preferences -> Keyboard.  There's another HP Pavilion laptop listed that you could select.  And you can always change it back.

---

### Post by Kaneda on 2006-03-30
Hmm... I tried a few different layouts, and none of them worked... Any other ideas?

---

### Post by MetalHannes on 2006-03-30
[http://linux.oneandoneis2.org/keys.htm]("http://linux.oneandoneis2.org/keys.htm")
You could define it as a hotkey.

---

### Post by Kaneda on 2006-03-30
Okay, I found the solution.  It was actually along the lines of what Barrakketh was saying when he said:
[quote=Barrakketh]The last time I checked laptop keyboards don't have 104 (or even 101) keys.[/quote]
The keyboard setup in System > Preferences > Keyboard was set as Generic 104-key PC.  I tried changing to some various notebook setups on the list to no avail, but when I changed to Generic 101-key PC, everything worked out fine. 

Thanks a lot everybody!

---

