---
title: "F10 opens network menu instead of doing what it's supposed to"
date: 2011-10-25
forum: General Help
---

### Post by macflav on 2011-10-25
I use a system that runs as a Java applet. I need the F10 key on the login screen, but when I press it, the network menu from the top ubuntu bar opens instead, so the applet window loses focus. Can't find a workaround, so I can't use the system!

Back to (yuck) Windows 7...

---

### Post by haqking on 2011-10-25
> **macflav said:**
> I use a system that runs as a Java applet. I need the F10 key on the login screen, but when I press it, the network menu from the top ubuntu bar opens instead, so the applet window loses focus. Can't find a workaround, so I can't use the system!

Back to (yuck) Windows 7...

add a keyboard shortuct, why does it need to be F10 ?

---

### Post by macflav on 2011-10-25
> **haqking said:**
> add a keyboard shortuct, why does it need to be F10 ?

The applet I need to use is a text terminal (sort of like an old BBS). There's no way of reconfiguring its shortcuts, so I do need the F10 key. It would be great if I could disable the F10 shortcut associated with Ubuntu's menus, but I didn't find a way to do it.

---

### Post by macflav on 2011-10-25
Here's a picture (worth a thousand words, right?), to make it clearer (couldn't do a PrintScreen with the calendar menu open):

[IMG]https://lh5.googleusercontent.com/-_7XmiUpm7Rg/TqdAWPl9t_I/AAAAAAAAAXE/7N8ebCyIpuQ/s720/2011-10-25%25252018.55.20.jpg[/IMG]

As you see, I need to use many "F" keys (F1, F3, F5, etc.). They all work fine, except for F10 (which now opens the calendar... earlier today it was the network menu between the bluetooth icon and the speaker icon).

---

### Post by haqking on 2011-10-25
mmm well i have never had the need to remap a F key, but xmodmap might work for you.

I havent got time to play with it right now but you might want to take a look at it.

Good luck

---

### Post by jwbrase on 2011-10-25
This appears to be a known bug in Unity.

[http://www.mjfox.ch/wordpress/ubuntu-11-04-unity-terminal-and-the-f10-key/](http://www.mjfox.ch/wordpress/ubuntu-11-04-unity-terminal-and-the-f10-key/)

From your screenshot, it appears that your program is an emulator for an IBM 3270 terminal. There is another such emulator in the Ubuntu repositories (at least as of Ubuntu 10.04, which I'm using), called x3270, and allows you to configure a keymap. You may be able to use this instead. You can get it through the Software Center.

(However, x3270 seems to respond to the mouse in a rather non-standard way: you need to click-and-hold on menus to get them to stay visible, and in the keymap configuration dialog, left click scrolls down through the list of key mappings and right-click scrolls up, rather than the standard way where you have a scrollbar that you left-click at the top or the bottom).

---

### Post by macflav on 2011-10-25
jwbrase, the solution offered on the page you referred me to (CompizConfig Settings Manager) worked beautifully. Now I'll try to figure out how to change this thread to [SOLVED]. :)

Thank you both (jwbrase and haqking) so much for taking your time to help a fellow linux fan!

---

### Post by haqking on 2011-10-26
> **jwbrase said:**
> This appears to be a known bug in Unity.

[http://www.mjfox.ch/wordpress/ubuntu-11-04-unity-terminal-and-the-f10-key/](http://www.mjfox.ch/wordpress/ubuntu-11-04-unity-terminal-and-the-f10-key/)

From your screenshot, it appears that your program is an emulator for an IBM 3270 terminal. There is another such emulator in the Ubuntu repositories (at least as of Ubuntu 10.04, which I'm using), called x3270, and allows you to configure a keymap. You may be able to use this instead. You can get it through the Software Center.

(However, x3270 seems to respond to the mouse in a rather non-standard way: you need to click-and-hold on menus to get them to stay visible, and in the keymap configuration dialog, left click scrolls down through the list of key mappings and right-click scrolls up, rather than the standard way where you have a scrollbar that you left-click at the top or the bottom).

nice, good to know

> **macflav said:**
> jwbrase, the solution offered on the page you referred me to (CompizConfig Settings Manager) worked beautifully. Now I'll try to figure out how to change this thread to [SOLVED]. :)

Thank you both (jwbrase and haqking) so much for taking your time to help a fellow linux fan!

col glad you got it sorted.

Peace

---

