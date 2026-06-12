---
title: "Missing close, minimize, restore buttons"
date: 2011-02-26
forum: General Help
---

### Post by akber on 2011-02-26
Hi everyone,

I'm running Ubuntu 10.10 and after trying several of the fixes that i have seen on the forums i still havent been able to get my window tab buttons back. I've tried several terminal commands and nxclient updates (although i didn't quite get how the nxclient thing worked so i didnt really follow through there). 

If updating or installing nxclient is the solution could someone please provide a how to on what to do to install it?

If there are any other solutions you know, i would be very grateful to hear them

---

### Post by sikander3786 on 2011-02-26
Please press Ctrl + F2 and type

```
metacity --replace
```

Is there any change?

---

### Post by akber on 2011-02-26
Thanks, Metacity plug in works, but my compiz settings got screwed up like the animations doesn't work, the visual effects automatically changed to none, and when i tried to put it on either one of the choices, the buttons are gone again...

Is there a another solution for this problem?

---

### Post by sikander3786 on 2011-02-26
In my own experience, these type of problems are common with Compiz. Don't take from it that Compiz is in any way unstable but yet the problems are there.

No proper solution in my knowledge. When it happens, you can either restart compiz by pressing Alt + F2 and typing,

```
compiz --replace
```

Or install fusion-icon from Software Center or apt-get. Start it from Applications > System Tools > Fusion Icon. It will sit in the system tray and you can use it to switch/restart you windows managers.

Applications > Accessories > Terminal:

```
sudo apt-get install fusion-icon
```

---

### Post by akber on 2011-02-26
i tried that command as well, but the buttons still doesn't show up...it wasn't like before until i tried to do some animations from compiz, and apparently it doesn't work, so i uninstalled it, then later on the animations are working, but then the buttons are missing...

Should i try to reinstall ubuntu?

---

### Post by sikander3786 on 2011-02-26
Re-install is an option but I would recommend to try fusion-icon first. I am sure you will get compiz and windows title bars working again.

---

### Post by akber on 2011-02-26
I tried that command as well, but it said that my fusion is already the latest version, and it's still not showing the buttons...

---

### Post by sikander3786 on 2011-02-27
Press Alt + F2 and type

```
fusion-icon
```

Can you see the icon in your notification area now?

---

### Post by pritam_par on 2011-08-10
Enable **Move window  **and **window Decoration  **in compiz setting manager. It will solve the issue

---

