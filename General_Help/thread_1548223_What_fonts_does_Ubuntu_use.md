---
title: "What fonts does Ubuntu use?"
date: 2010-08-08
forum: General Help
---

### Post by lwalper on 2010-08-08
What kind of fonts does Ubuntu use? As a newbie I tried using Gimp and changing the type faces - they all look about the same. Sure, there are serifs and san serifs, but other than that, even the dingbats displayed in a san serif face. Does Ubuntu use truetype, open type, or what? I searched the archives for font entries and came up with -0- relevant entries.

---

### Post by Ginsu543 on 2010-08-08
Ubuntu primarily uses TrueType fonts. Besides the default fonts, you can add TrueType fonts by copying .ttf files to the .fonts folder in your home folder (if it's not there, you can just create it).

---

### Post by lwalper on 2010-08-08
OK. Thanks, I'll give that a try. I notice there's a fonts folder in the etc folder with a couple of files in it, but no fonts that I can tell. When I "install" fonts where do they go? I've installed quite a few by double clicking on the font file and then clicking the install button. They seem to work, but have disappeared in the directory tree.

---

### Post by Vaphell on 2010-08-08
```
locate .ttf
```

majority is in /usr/share/fonts on my system

---

### Post by Ginsu543 on 2010-08-08
If you want the fonts to be available to every user (assuming you have multiple users), just copy the .tff files to the /usr/share/fonts folder. If you want the fonts available only to you or to a particular user, copy the .tff files to the home/*user name*/.fonts folder for each user. Notice the period in front of fonts, which means that .fonts is a hidden folder inside the home folder. You will have to hit CTRL+H to make hidden files visible to see it. If it is not there, just create one.

You don't have to "install" these fonts. Just copying them to the appropriate folders will "install" them so that the OS can see them and use them. When you clicked on the "Install" button, it most likely copied the font to either the /usr/share/fonts folder or the .fonts folder inside your home folder. In other words, the "Install" button just did the copying for you. So if you want to see the fonts you installed, just check out those two locations.

One more thing, the /usr/share/fonts folder is permission protected, while .fonts is not. This means that, to copy files to /usr/share/fonts, you need super-user (administrative) rights. So in Terminal, you need to use "sudo cp" and enter your password (or if you want to use Nautilus, you must first launch it using "gksu Nautilus" in Terminal and entering your password).

---

### Post by lwalper on 2010-08-29
I just dumped a bunch of OpenType fonts in my /home/fonts folder. Ubuntu must not use that font type. They don't seem to work - actually don't even show in the font list as usable. Guess I'll have to look around for a substitute in the TTF format.

---

### Post by Vaphell on 2010-08-29
proper dir is ~/.font - with a dot

besides you can double click a ttf file to open a font browser and there is a button that says 'install'
it will put the font in the proper place for you, you try to make it harder than it is ;-)

---

### Post by Bachstelze on 2010-08-29
> **Vaphell said:**
> proper dir is ~/.font**s** - with a dot

Fixed that for you. Or /usr/share/fonts if you want the font to be available to all users.

---

### Post by Vaphell on 2010-08-29
lol, my bad :)

---

