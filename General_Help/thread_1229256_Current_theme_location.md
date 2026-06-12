---
title: "Current theme location"
date: 2009-08-01
forum: General Help
---

### Post by Muscovy on 2009-08-01
I was wondering where the core config files is that says X normal or X custom theme is selected. I know it'll be in ~/, and I assume it's in ~/.gconf, somewhere.

---

### Post by credobyte on 2009-08-01
What do you mean by "X normal" and "X custom" ? Anyway, all themes can be found at [COLOR=DimGray]/usr/share/themes[/COLOR] !

---

### Post by Muscovy on 2009-08-02
I mean the file that tells Ubuntu what theme is being used. If I set my theme to Clearlooks, or Darkroom, that fact is recorded somewhere.

  X was a rather poor example, just ignore it,

---

### Post by credobyte on 2009-08-02
Terminal:
```
cd ~/.gconf/desktop/gnome/interface && cat %gconf.xml
```

Output:
```
<?xml version="1.0"?>
<gconf>
    <entry name="icon_theme" mtime="1249136936" type="string">
        <stringvalue>Breathe</stringvalue>
    </entry>
    <entry name="gtk_theme" mtime="1249136637" type="string">
        <stringvalue>Dust Sand</stringvalue>
    </entry>
</gconf>
```
A lil bit of parsing and you're ready to go :)

---

### Post by Muscovy on 2009-08-02
Doesn't seem to do what I want. I want to make a program that can toggle between pre-set themes. The file does exactly what you said, though for example if I make the theme Human in the xml file, nothing changes. Is there anything higher up? Or, even better, can themes be applied in terminal? I could do that with the C++ system() command.

---

### Post by Muscovy on 2009-08-15
Bump.

I'm getting fairly annoyed at it, because I made a program that switches the wallpapers when you press Ctrl-B, but I still can't find a way to do themes.

---

### Post by CatKiller on 2009-08-15
> **Muscovy said:**
> Or, even better, can themes be applied in terminal?

Use gconftool-2 to set GConf values from the command line. It'll be something like ```
gconftool-2 --type=string --set  /desktop/gnome/interface/gtk_theme "CaseSensitiveNameOfTheme"
``` Do the same for ../icon_theme and /apps/metacity/general/theme. Check **man gconftool** for the exact syntax; I'm on KDE atm, so I can't check it for you.

If you're doing a Python script, Python has its own gconf bindings that you could use instead.

---

### Post by Muscovy on 2009-08-15
Thanks, the first two work, I've just gotta find the path of the icons.

---

### Post by CatKiller on 2009-08-15
> **Muscovy said:**
> Thanks, the first two work, I've just gotta find the path of the icons.

How do you mean? User icon themes are in ~/.icons. System-wide icon themes are in /usr/share/icons.

---

### Post by Muscovy on 2009-08-15
[del]I mean the filepath for setting the icons with gconftool.[/del

Never mind, got it, thank you!

---

### Post by CatKiller on 2009-08-16
I did say.  /desktop/gnome/interface/icon_theme. Glad you found it though.

---

