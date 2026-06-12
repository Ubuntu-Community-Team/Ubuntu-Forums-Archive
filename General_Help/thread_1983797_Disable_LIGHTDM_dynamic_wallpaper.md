---
title: "Disable LIGHTDM dynamic wallpaper"
date: 2012-05-20
forum: General Help
---

### Post by DarkBowser on 2012-05-20
I hate the way the lightdm wallpaper in 12.04 changes to the user background. I have already tried to use dconf editor to disable the "draw user background" option for lightdm. How can I manually stop the lightdm from using my background so I can set a static one?:-(

---

### Post by HunterDX77M on 2012-05-25
Bump. I'm interested in this too.

---

### Post by uflieven on 2012-05-25
[FONT="Courier New"]In a terminal window, enter the following command:

**When using Ubuntu:**
```
[COLOR="Blue"]sudo nano /etc/lightdm/unity-greeter.conf[/COLOR]
```

**When using Xubuntu or Lubuntu:**
```
[COLOR="blue"]sudo nano /etc/lightdm/lightdm-gtk-greeter-ubuntu.conf[/COLOR]
```

**For Kubuntu**, it should be something similar, but I haven't got the exact name of the file.

Then, on about line 12, after the word background= you should remove everything on that line
after the equal sign and type a color code or an image path instead.

e.g.```
[COLOR="blue"]#0000FF[/COLOR]
```

This will change the login screen to blue.

Or, you can use an image path, for example if you have an image lake.png
in your home folder, you should type the following

```
[COLOR="blue"]~/lake.png[/COLOR]
```

The ~ in the previous command is a substitution for /home/<username>. It will set the file
lake.png as background.

Then press Ctrl+x to save and exit.[/FONT]

---

