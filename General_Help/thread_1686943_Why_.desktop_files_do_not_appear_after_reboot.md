---
title: "Why .desktop files do not appear after reboot?"
date: 2011-02-13
forum: General Help
---

### Post by stchman on 2011-02-13
Hello all, I hace used this .desktop entry in the past with success:

```

[Desktop Entry]
Version=1.0
Name=Microsoft Freecell
GenericName=Game
Comment=Play Microsoft Freecell
Exec=msfreecell
Icon=/opt/msfreecell/msfreecell_icon.png
StartupNotify=true
Terminal=false
Type=Application
Categories=Game;

```

When I create the msfreecell.desktop file it appears under the Games section.

If I reboot the workspace CTRL-Alt-Bksp the entry is no longer in the Games secion of the Applications menu.

This has worked in Karmic, has anything changed in Ubuntu since?  I currently use Lucid.

Thanks.

---

### Post by stchman on 2011-02-14
Bump.

---

### Post by stchman on 2011-02-16
Bump.

---

### Post by stinkeye on 2011-02-16
I had a similar problem when editing a .desktop file and the solution given to me
was I needed to rebuild the applications cache with
```
sudo dpkg-reconfigure python-gmenu
```
Then log in/out.

---

### Post by stchman on 2011-02-16
> **stinkeye said:**
> I had a similar problem when editing a .desktop file and the solution given to me
was I needed to rebuild the applications cache with
```
sudo dpkg-reconfigure python-gmenu
```Then log in/out.

I will give that a try when I get home.  Thing is is that is doesn't do it on all my Ubuntu/Mint machines.

---

### Post by stinkeye on 2011-02-16
I don't understand it either.
I had performed the same edit before on a screensaver .desktop file
and it worked without running the command.

---

