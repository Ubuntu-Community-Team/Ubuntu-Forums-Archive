---
title: "Issues list"
date: 2011-12-19
forum: General Help
---

### Post by nnn= on 2011-12-19
ubuntu 10.10

I don't expect solutions, but posting issues publicly might incline someone to fix them. Also, these notes don't represent the full scope of the issues, but I think it's still important to note them so as to indicate a need for improvement. Certainly with greater expertise some things could be understood better, but I have current understanding. They are however not so significant as to research them individually.

gnome should fix printscreen, it doesn't work unless cursor is in some specific place; Alt+Print Screen not working at all (even though sysrq=0); it should copy straight to clipboard or offer command option to do so.

metacity gets broken and windows cannot be switched requiring restart, since no commands can be run in current terminal. I don't know how to indicate from another virtual terminal to restart metacity on current terminal.

gimp should improve by a lot, has terrible usability

---

### Post by mikewhatever on 2011-12-19
Hm..., and how does one fix 'metacity gets broken...', and gimp should improve?

---

### Post by 3rdalbum on 2011-12-19
1. Have you tried simply "Printscreen" without the Alt key? You can also run the "Take a Screenshot" program manually from the Applications menu.

2. You could add a launcher to your panel with the command "metacity --replace". When you lose the window borders, click the launcher and the window manager will start up again. It's possible to create a launcher for "metacity" even without use of your keyboard, but you have to navigate to /usr/bin to find it.

Alternatively, you could use the Appearance program to turn on Desktop Effects, which is actually a different window manager altogether (Compiz).

3. Use a newer version of Ubuntu; the window management in Gimp is better in newer versions, and works a lot like Photoshop (the Mac version). The toolbox and layers palettes are still in separate windows like on the Mac, but they hide when another program is in the foreground.

---

### Post by nnn= on 2011-12-19
You people have wonderfully uplifted my outlook, for I did not expect any replies. :D

When metacity breaks it could restart on its own. It should detect that it's not working properly.
Creating an icon for "metacity --replace" is a great idea. I tried to create it when I couldn't use keyboard, but that didn't work, and this would. If I just browsed to metacity and couldn't type "--replace" would that still work?

Yes printscreen without alt works, but I had to edit the pic later, which is why I brought up gimp. I then installed mtpaint, and due to being simpler, it worked better. Also, printscreen doesn't work at all in such instances as when the cursor is choosing among color boxes.

Gimp hides the picture while I move it, it doesn't maximise the window or the viewing area on start. I suppose that's because it doesn't fit in 640x480, but then it should resize. Perhaps this can be easily remedied within gimp, but it didn't look that way when I was using it.

A newer version (11) has bad reviews and doesn't overall seem to be an improvement, so I think gimp doesn't make it worth upgrading.

---

