---
title: "GTK can't find icon for Colorcode"
date: 2011-03-23
forum: General Help
---

### Post by jesuisbenjamin on 2011-03-23
Hi there,

I'm editing some icons for a set that's missing a few programs. I've done several program icons this way, without trouble. Starting from a SVG, i check the proper name for the icon (by assigning it to the program's tray icon in Cairo-Dock, which automatically copies the original and renames that as it should be.). Then i create a copy in 48, 32, 24, 22, 16 pixel sizes, move them into the /usr/share/icons/ICONSET folder and voilà.

For some reason after i created an icon for Colorcode, GTK does not pick up the icon in Ubuntu menus nor in Synapse. The name of the icon, from all the sources i've been able to find, seems to be simply "colorcode". 

Any idea as to why this icon can't be identified / assigned?

Thanks.

Benjamin

---

### Post by Krytarik on 2011-03-23
Glad to hear that I'm apparently not the only one who undertakes the effort to modify an icon theme by himself! As for the icon, I can't find an image with that or a similar name in any of my installed icon themes. Could you please say where exactly you see those icon (except for Synapse, because I don't have it installed)?

Greetings.

---

### Post by jesuisbenjamin on 2011-03-23
Hi there,

Yes i am trying to update Faenza with some of the programs i use, especially those with ugly, low resolution icons, like Colorcode.

The original icon of Colorcode appears in the Gnome Menu Games > Colorcode and in Cairo-Dock when the program is launched. But i believe you think i am modifying an existing icon for Colorcode, which is not the case. I created it from scratch.
GTK however uses a colorcode32.xpm in the /usr/share/pixmaps/ (I assume the "32" in this filename refers to the size of the icon, but now i am wondering whether i should not name my own icon this way too...)

---

### Post by Krytarik on 2011-03-23
Ok, thanks for the hint that it's actually a game. I just yet checked it's package from the official repos and it indeed turned out that it includes the image "/usr/share/pixmaps/colorcode32.xpm", which it uses by default, and solely.
```
[Desktop Entry]
Version=1.0
Name=ColorCode
Comment=Advanced clone of the MasterMind code-breaking game
GenericName=Clone of the MasterMind code-breaking game
GenericName[fr]=Clone avancé du jeu MasterMind
TryExec=/usr/games/colorcode
Exec=/usr/games/colorcode
Terminal=false
Icon=/usr/share/pixmaps/colorcode32.xpm
Type=Application
Categories=Qt;Game;LogicGame;

```
So, in order the make it to use your created image, especially also as app icon, you need to replace those. It needs to be the same size 32x32 pixels, but you can retain the PNG format, just rename it as xpm.

---

### Post by jesuisbenjamin on 2011-03-24
Hi there!

How did you get this info output on the package?
So i have to convert it to xpm? It seems so weird to me that a program should chose the icon-theme for itself, independently from my desktop environment.
If every program would do that, there would not be much point in making icon themes, would it?

Well thanks for researching this then. Cheers!

B.

---

### Post by Krytarik on 2011-03-24
> **jesuisbenjamin said:**
> 
How did you get this info output on the package?
I downloaded its package from here: [http://packages.ubuntu.com/maverick/colorcode](http://packages.ubuntu.com/maverick/colorcode) and opened it with Archive Manager.
But you could simply open its .desktop-file in "/usr/share/applications".
> **jesuisbenjamin said:**
> 
So i have to convert it to xpm?
Nope, like I said before. If it doesn't use it also as app icon, you could also retain your image size and its name, and modify the .desktop-file instead.
> **jesuisbenjamin said:**
> It seems so weird to me that a program should chose the icon-theme for itself, independently from my desktop environment.
If every program would do that, there would not be much point in making icon themes, would it?

Exactly. But it seems that this is only the case for not so common apps, which otherwise would end up with having no icon at all.

---

### Post by jesuisbenjamin on 2011-03-24
Mmh ... then i am not sure what i did wrong. 
I sudo-edited the /usr/share/applications/desktop.en_US.utf8.cache file with:

```
[colorcode]
Name=ColorCode
GenericName=Clone of the MasterMind code-breaking game
Comment=Advanced clone of the MasterMind code-breaking game
Icon=colorcode
Exec=/usr/games/colorcode
TryExec=/usr/games/colorcode
Terminal=false
Type=Application
Categories=Qt;Game;LogicGame;
```

And yet GTK keeps showing the XPM file...

---

### Post by Krytarik on 2011-03-24
First, you should modify its .desktop-file instead, and then run those commands to update the menu item cache:
```
rm /usr/share/applications/desktop.*.cache
sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"

```
Then restart gnome-panel to make it read the cache file:
```
killall gnome-panel
```

---

### Post by jesuisbenjamin on 2011-03-24
Ha!

I finally made it. See i got confused because the desktop's file's full name is colorcode.desktop, while nautilus shows no .desktop extension. So editing the file without mentioning its extension created an empty file instead.

For further users: 

[LIST=1]
[*]Type the code:
```
sudo gedit /usr/share/applications/colorcode.desktop
```

[*]And change the [FONT="Courier New"]icon[/FONT] attribute to add the value [FONT="Courier New"]colorcode[/FONT].

[*]Then update cache according to post here above.
[/LIST]

Thanks to Krytarik :)

---

### Post by Krytarik on 2011-03-24
> **jesuisbenjamin said:**
> 
See i got confused because the desktop's file's full name is colorcode.desktop, while nautilus shows no .desktop extension.
In fact, it does:
```
krytarik@krytarik-desktop:/usr/share/applications$ ls nautilus*
nautilus-autorun-software.desktop  nautilus.desktop
nautilus-browser.desktop           nautilus-file-management-properties.desktop
nautilus-browser-root.desktop      nautilus-folder-handler.desktop
nautilus-computer.desktop          nautilus-home.desktop
krytarik@krytarik-desktop:/usr/share/applications$ 

```However. ;-)
> **jesuisbenjamin said:**
> Then update cache according to post here above, or simply reboot.
In fact, simply rebooting doesn't help, you need to update the cache file.

---

### Post by jesuisbenjamin on 2011-03-25
OK,

I'll trust you on the cache and edit my previous post. Though i simply rebooted, and it worked out for me.

As to the .desktop extension i meant that using the file browser "Nautilus", i am not able to see the .desktop extension, but merely the file name. The only way to find out the extension is to open the file's properties or use Terminal as you did. This is where the confusion came from.

Cheers,
Benjamin

---

### Post by Krytarik on 2011-03-25
> **jesuisbenjamin said:**
> 
I'll trust you on the cache and edit my previous post. Though i simply rebooted, and it worked out for me.
With the menu items / cache file it's that way: When you modify a .desktop-file, the changes come immediately into effect. But when you relogin/reboot the changes get reverted due to the cache file. And those cache file gets updated either when a package which includes a .desktop-file for that directory gets installed/upgraded or when you update it manually, by running the stated commands.
> **jesuisbenjamin said:**
> As to the .desktop extension i meant that using the file browser "Nautilus", i am not able to see the .desktop extension, but merely the file name. The only way to find out the extension is to open the file's properties or use Terminal as you did. This is where the confusion came from.
Ah, now I understand, that's pretty obstructive, you also can't right-click at them and open them in gedit. I didn't find a way to make that possible so far.

---

