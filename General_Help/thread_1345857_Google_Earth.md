---
title: "Google Earth"
date: 2009-12-04
forum: General Help
---

### Post by usmanasim on 2009-12-04
Hello Ubuntu people.

I just installed Google Earth form their website. But how do you run the
Software. I cannot find any shortcut anywhere.

---

### Post by Vishnu V on 2009-12-04
Did u installed it properly?

You can locate it from applications->Internet->GoogleEarth

---

### Post by t0p on 2009-12-04
Normally, when you install Google Earth, an entry for it is created at **Applications > Internet**.  If it's not there, right-click on the top panel where it says "Applications" and select to edit menus.  Look at Applications > Internet to see if there's an unchecked entry for Google Earth.  If it's there, check the box and close the window.  Now check Applications > Internet again - Google Earth should be there.

If that's no good, you can start the program by hitting **Alt+F2** and typing into the box *googleearth*.  Or you can create a launcher on the panel to run command:

```
/usr/local/bin/googleearth
```

Well, that's where Google Earth is on my computer.  Yours may differ - find out by typing into a terminal:

```
which googleearth
```

---

### Post by blondee.elizabeth on 2009-12-04
the people in ubuntu will tell you not to do this but if you install ubuntu tweak it will install it for you properly, and many other wonderful programs as well.

---

### Post by blur xc on 2009-12-04
You can also install it from the (IIRC) medibuntu repositories.

BM

---

### Post by juliobahar on 2009-12-04
> **blondee.elizabeth said:**
> the people in ubuntu will tell you not to do this but if you install ubuntu tweak it will install it for you properly, and many other wonderful programs as well.

I agree with ubuntu tweak. Easier for me at least.

---

### Post by khelben1979 on 2009-12-04
Open up the directory where Google Earth is installed to. Then make a short cut from inside that directory to your desktop. On my system it's marked to not be executable since it's actually a script file.

Just right click on the icon and untick the executable flag to get it working.

---

### Post by scouser73 on 2009-12-04
You can follow the instructions here for installing Google Earth, [[COLOR="Red"]**Install Google Earth In Ubuntu**[/COLOR]]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/").  Ubuntu Tweak is an excellent piece of software for installing stuff, and I would recommend it also.

---

