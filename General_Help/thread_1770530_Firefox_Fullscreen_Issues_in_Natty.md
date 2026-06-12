---
title: "Firefox Fullscreen Issues in Natty"
date: 2011-05-29
forum: General Help
---

### Post by AlexanderDomin on 2011-05-29
Hey everybody,

I've been having some issues with my Firefox; I've searched through the forums and I can't seem to find anything pertaining to my exact situation. I recently did a clean install of Natty on my Eee-1018P netbook, and I'm using the GNOME 2 environment. When I first started Firefox, it popped up in a regular-sized window. I switched to fullscreen view with no problems, but when I clicked the "restore" button in the top right- rather than switching back to a windowed view- Firefox remained in fullscreen. The only difference was this time the toolbar was visible in the top of the screen.

I know that's difficult to understand, attached are pictures of what  I'm trying to describe. The first picture is a screencap of the  fullscreen view, the second picture is a screencap the supposedly  windowed view.

To summarize, I can't see the GNOME panel at the top of the screen, I can't switch between windows without using alt-tab, and I can't change Firefox back into a windowed view. God forbid I get a pop-up dialog; I have to press ctrl-alt-del, right-click the pop-up on the taskbar at the bottom of the screen, and select "close". Pressing F11 does nothing, it merely switches between the two fullscreen views. Restarting Firefox doesn't help either, it only started in an actual window the very first time. I've tried a complete reinstall of Firefox as well, to no avail.

Can anyone help me out?

---

### Post by wildmanne39 on 2011-05-29
> **AlexanderDomin said:**
> Hey everybody,

I've been having some issues with my Firefox; I've searched through the forums and I can't seem to find anything pertaining to my exact situation. I recently did a clean install of Natty on my Eee-1018P netbook, and I'm using the GNOME 2 environment. When I first started Firefox, it popped up in a regular-sized window. I switched to fullscreen view with no problems, but when I clicked the "restore" button in the top right- rather than switching back to a windowed view- Firefox remained in fullscreen. The only difference was this time the toolbar was visible in the top of the screen.

I know that's difficult to understand, attached are pictures of what  I'm trying to describe. The first picture is a screencap of the  fullscreen view, the second picture is a screencap the supposedly  windowed view.

To summarize, I can't see the GNOME panel at the top of the screen, I can't switch between windows without using alt-tab, and I can't change Firefox back into a windowed view. God forbid I get a pop-up dialog; I have to press ctrl-alt-del, right-click the pop-up on the taskbar at the bottom of the screen, and select "close". Pressing F11 does nothing, it merely switches between the two fullscreen views. Restarting Firefox doesn't help either, it only started in an actual window the very first time. I've tried a complete reinstall of Firefox as well, to no avail.

Can anyone help me out?
Hi, when you have firefox open and that happens try f11 and see if that fixes it, if not hit f11 again to restore to previous state.

---

### Post by AlexanderDomin on 2011-05-29
Pressing F11 just toggles between the two views pictured in the attached screencaps; Firefox stays fullscreen.

It should be noted that in the second screencap, the minimize, restore, and close buttons are gone out of the top-right corner, just as they would be if it were running in a window. For all intents and purposes, it acts like I've switched from true fullscreen to a window that's just slightly larger than my monitor screen.

---

### Post by wildmanne39 on 2011-05-29
> **AlexanderDomin said:**
> Pressing F11 just toggles between the two views pictured in the attached screencaps; Firefox stays fullscreen.

It should be noted that in the second screencap, the minimize, restore, and close buttons are gone out of the top-right corner, just as they would be if it were running in a window. For all intents and purposes, it acts like I've switched from true fullscreen to a window that's just slightly larger than my monitor screen.
That is what it looked like. You might do a complete uninstall of it in synaptic then reinstall.

---

### Post by AlexanderDomin on 2011-05-29
I've tried that too, Firefox starts in fullscreen and acts the same. Also, I tried switching to Unity and running Firefox in that environment and it did the same thing. It's all very confusing.

---

### Post by AlexanderDomin on 2011-05-29
I believe I've fixed it. There's a package called firefox-gnome-support that apparently didn't come pre-installed with Natty. I found it in the Software Center under Firefox's add-ons tab and installed it, and so far everything seems to be working exactly as I hoped it would. Thanks for the help!

Cheers,
Alexander

---

### Post by wildmanne39 on 2011-05-29
> **AlexanderDomin said:**
> I believe I've fixed it. There's a package called firefox-gnome-support that apparently didn't come pre-installed with Natty. I found it in the Software Center under Firefox's add-ons tab and installed it, and so far everything seems to be working exactly as I hoped it would. Thanks for the help!

Cheers,
AlexanderHi, thats great glad you got it fixed.

---

