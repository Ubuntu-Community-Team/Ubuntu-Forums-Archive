---
title: "How to run installed program on kubuntu"
date: 2009-08-28
forum: General Help
---

### Post by shanali4 on 2009-08-28
[SIZE=3]I have installed GIMPShop from a debian package downloaded from their official website. It's installed successfully but how to install the GIMPShop. Their are no traces in start menu. Plz help how to run it.

I M new to linux. and switched to it from windows. so i m confused:lolflag:
[/SIZE]

---

### Post by esalnoj on 2009-08-29
Use the file search function to search **filesystem** for **GIMPShop**.

You should see a "GIMPShop" shell script (a file with gears inside a diamond on it) or a "GIMPShop.sh" file.

Then type the following terminal command, and leave it in your .bash_history file:
```
cd "filepath/where/shell/script/is" && ./"GIMPShop_shell_script"
```

Replacing the qoutation mark sections with whatever shows up in the search result.

Then, when you want to run GIMPShop, all you have to do is open terminal and press down arrow until you find your command, press enter.

If you have permissions error, try this command instead:
```
cd "filepath/where/shell/script/is" && sudo ./"GIMPShop_shell_script"
```

again replacing the qoutation mark sections with what shows in your search result.

---

### Post by shanali4 on 2009-08-29
> **esalnoj said:**
> Use the file search function to search **filesystem** for **GIMPShop**.

You should see a "GIMPShop" shell script (a file with gears inside a diamond on it) or a "GIMPShop.sh" file.

Then type the following terminal command, and leave it in your .bash_history file:
```
cd "filepath/where/shell/script/is" && ./"GIMPShop_shell_script"
```Replacing the qoutation mark sections with whatever shows up in the search result.

Then, when you want to run GIMPShop, all you have to do is open terminal and press down arrow until you find your command, press enter.

If you have permissions error, try this command instead:
```
cd "filepath/where/shell/script/is" && sudo ./"GIMPShop_shell_script"
```again replacing the qoutation mark sections with what shows in your search result.
[SIZE=3]
GIMPShop.sh file not found plz help[/SIZE]

---

### Post by warreno on 2009-08-29
> **shanali4 said:**
> [SIZE=3]
GIMPShop.sh file not found plz help[/SIZE]

For what it's worth you're not going crazy — I just DLed the same package (Debian GimpShop) to my Ubuntu 9.04 install, and I can't find it either after running the package.

Their user forums, by the way, appear to be — at best — lackadaisically policed. At least half the posts on the *first page* are spam for porn sites. Searching there for "Ubuntu" yields no results.

In going to what appears to be the original site for GIMPshop, [PlasticBugs]("http://plasticbugs.com/?page_id=294"), I seem to see that this app hasn't been updated since *2006*. That leads me to believe, very strongly, that it's not going to work with Ubuntu, or at least not any Ubuntu with a version number higher than about 6 or 7.

For what it's worth I watched the install progress (clicking the disclosure triangle let me see it) and it looked like the .deb package was trying to write a GIMP version **2.2** to /usr/bin. Well, the *current* GIMP version is **2.6**. My assumption is twofold:

1. The installer will not replace a newer version of GIMP with an older one; and

2. The installer fails silently — that is, it doesn't say the installation was unsuccessful.

If you're feeling bold, you could try going into Applications -> Add/Remove and deleting your current install of GIMP, then running the GIMPshop installer again to see if that gets you what you want.

This may not be the best course, though, since it's possible you'll be installing a version of the GIMP that's about three years out of date now.

---

### Post by fluffman86 on 2009-08-29
GimpShop was really designed to give a single window gimp experience for Mac and Windows.  You can essentially recreate this by just going to another workspace (one of the 4 little squares in the bottome right on the taskbar) before running Gimp.

edit: you might also want to check out:
[http://penguininside.blogspot.com/2009/08/using-gimp-as-single-window-tabs-and.html](http://penguininside.blogspot.com/2009/08/using-gimp-as-single-window-tabs-and.html)
or [http://ubuntuforums.org/showthread.php?t=240543](http://ubuntuforums.org/showthread.php?t=240543)

---

