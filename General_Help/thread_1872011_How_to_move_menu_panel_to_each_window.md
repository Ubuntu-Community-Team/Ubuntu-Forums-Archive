---
title: "How to move menu panel to each window?"
date: 2011-10-29
forum: General Help
---

### Post by boy18nj on 2011-10-29
Basically I want to move menu (File Edit View History Tools Help) from top panel to each window level(like Windows Vista). Current it is at the top panel(like Mac OSX).

Also my shortcut key Alt + F is not working.

Any ideas here?

---

### Post by fikr4n on 2011-10-29
Did you mean in Unity?

---

### Post by stinkeye on 2011-10-30
On 11.10
Enter in the terminal
```
echo '[ "$DESKTOP_SESSION" = "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

Log out/in.

To revert back to using the global menu simply remove the file at /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

> Also my shortcut key Alt + F is not working.
Not sure about the alt+F shortcut.
What's it supposed to do?

---

### Post by boy18nj on 2011-10-30
Thanks, but I tried it. Still the menu panel is at the top of the screen instead of each individual window.

I know in past, I've done this using GUI tool only, now I don't rem how I did that.

---

### Post by gandaran on 2011-10-30
> **boy18nj said:**
> Thanks, but I tried it. Still the menu panel is at the top of the screen instead of each individual window.

I know in past, I've done this using GUI tool only, now I don't rem how I did that.
did you reboot?
you could remove the global menu completely too if that doesn't work, find instructions here
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by boy18nj on 2011-10-30
Thanks for reply. I did logout only as suggested earlier.

In the link mentioned, I tried, Right click on global menu and click remove from panel. It worked.

Thank you all guys.

---

### Post by stinkeye on 2011-10-30
I'm a bit lost here.
What the fix is for is moving the File edit menu back into the actual running app instead of being in the panel.
It is for when your logged into an "ubuntu" session....ie Unity with compiz.

You don't run the second command
**sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy**
 ...that will set it back to how it was.


When ran in the terminal this tells you what session your logged in to...
```
echo $DESKTOP_SESSION
```

---

