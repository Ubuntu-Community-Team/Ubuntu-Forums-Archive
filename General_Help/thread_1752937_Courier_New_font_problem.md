---
title: "Courier New font problem"
date: 2011-05-08
forum: General Help
---

### Post by X5! on 2011-05-08
Hello everybody!

Yesterday I installed Ubuntu 11.04 on my laptop and I'm very exited. Since I need to do some programming, I downloaded Eclipse and Courier New font (since I am used to it). But unfortunately it looks like the font is kind of messed up.

Let's see some pics:
Courier New size 9 @ Windows 7:
[IMG]http://i54.tinypic.com/fuyr15.png[/IMG]


Courier New size 9 @ Ubuntu with default settings:
[IMG]http://i51.tinypic.com/rw841c.png[/IMG]


Courier New size 9 @ Ubuntu with confs:
[IMG]http://i51.tinypic.com/vglvv8.png[/IMG]
Things I changed:

~/.Xresources :
```

Xft.antialias:  true
Xft.hinting:    true
Xft.hintstyle:  hintfull
Xft.lcdfilter:  lcddefault
Xft.rgba:       rgb

```

and also I set Appearance -> Fonts -> Hinting to Full.

As you can see, there's still a difference. Keywords on the first picture are actually bold. In my last picture they are "too bold" to me and also if you look carefully for example letters "r", "c" and so on you can see that some parts of them are not so perfect.

My question is, what do I have to configure in ~/.fonts.conf to get the result which is as identical to win7 as it can get.

---

### Post by Vishnu V on 2011-05-08
To change font of eclipse editor
Goto Window -> Preferences
Then navigate to  general->Appearance->Colors and fonts
Expand java and change font of java editor by double click on it

---

### Post by X5! on 2011-05-08
> **Vishnu V said:**
> To change font of eclipse editor
Goto Window -> Preferences
Then navigate to  general->Appearance->Colors and fonts
Expand java and change font of java editor by double click on it

Yes, I know how to change font for Eclipse, it's just that my favorite monospaced font is messed up in Ubuntu.

---

