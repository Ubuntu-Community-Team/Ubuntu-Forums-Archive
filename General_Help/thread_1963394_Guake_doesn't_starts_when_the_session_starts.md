---
title: "Guake doesn't starts when the session starts"
date: 2012-04-22
forum: General Help
---

### Post by PauGNU on 2012-04-22
Hi,

Edit: Solution here: [http://ubuntuforums.org/showpost.php?p=11916239&postcount=8](http://ubuntuforums.org/showpost.php?p=11916239&postcount=8)

I'm using Ubuntu 12.04 with Gnome Shell. I've added guake to the startup programs, but it doesn't start when the session starts. It's weird, because I have no problems with other programs. But in guake's case, it doesn't work.

The order to start it up is: «guake». Actually, if I type «guake» in a terminal, then guake starts.

Any idea on this? Maybe I can take a look at the log, but I have no idea of its location.

Thanks!

---

### Post by compmodder26 on 2012-04-26
Same issue for me.  Works great in Unity, but not in Gnome Shell.  Works like a charm after I start it manually, but flat out refuses to autostart.

---

### Post by Biotico on 2012-04-29
I also encountered the same issue after doing a clean install (Ubuntu 12.04 64bits)

---

### Post by vjkeito on 2012-05-01
Anyone found a way to fix this?  

So much for stable LTS.  I've had nothing but issues.

---

### Post by mastablasta on 2012-05-01
> **vjkeito said:**
> Anyone found a way to fix this?  

the first post suggest that launching it form terminal works.
> 
So much for stable LTS.  I've had nothing but issues.


you do knwo that stable only means that bugs are known and crashes predictable?

---

### Post by CatmanIX on 2012-05-05
> **mastablasta said:**
> the first post suggest that launching it form terminal works.

That doesn't really fix the problem though. The problem is that it won't run on startup.

---

### Post by vjkeito on 2012-05-07
> **mastablasta said:**
> the first post suggest that launching it form terminal works.

Is that a joke?  Why would I want to launch it from a terminal?  I could just as easily hit alt+f2 and skip the terminal part.  The point is, that is not an auto-start.  I have to do that action EVERY BOOT.  Which is damn annoying.

---

### Post by PauGNU on 2012-05-08
SOLVED!!!

It seems that the entry automatically created by Guake is wrong. So we need to edit the autostart file. It's easy, just:

```
gedit /home/your_user/.config/autostart/guake.desktop
```

Remove everything and put this:

```
[Desktop Entry]
Name=Guake Terminal
GenericName=Guake Terminal
Comment=Guake Terminal
Exec=guake
Terminal=false
Type=Application
Icon=/usr/share/pixmaps/guake/guake.png
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=false
```

Then restart the computer/session!

Hope this helps!!!

---

### Post by xybrdragon on 2012-05-18
This did not fix this issue for me. Is anyone else still having an issue after this solution?

EDIT: This fixed my issue.

From Guake Preferences, uncheck "enable popup notifications on startup".

---

### Post by compmodder26 on 2012-05-18
No luck for me either.

---

### Post by siliconmeadow on 2012-05-25
> **xybrdragon said:**
> From Guake Preferences, uncheck "enable popup notifications on startup".
Worked for me too. Thanks!

---

### Post by Gwaro on 2012-08-11
> **xybrdragon said:**
> This did not fix this issue for me. Is anyone else still having an issue after this solution?

EDIT: This fixed my issue.

From Guake Preferences, uncheck "enable popup notifications on startup".


Unchecking 'enable popup notifications' worked for me too! Thanks alot.

---

### Post by figure002 on 2013-03-05
I can confirm that [[COLOR=#000000]xybrdragon[/COLOR]]("http://ubuntuforums.org/member.php?u=280658")'s solution works (unchecking "enable popup notifications on startup").

---

