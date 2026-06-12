---
title: "Any password managers with an indicator?"
date: 2012-07-14
forum: General Help
---

### Post by Stray Wolf on 2012-07-14
I decided to use a password manager and went with keepassx since it came highly recommended. Problem is it has no indicator applet that I've found, so it always has to be on-screen or minimized. So, when I use alt+tab I always have to cycle past it. Is there a way to avoid this? Preferably an indicator, or a script that will exclude keepassx from being in the alt-tab cycle or...anything.

---

### Post by wallaroo on 2012-07-14
You need to go to 'Extras -> Settings' and tick .. 
[INDENT]*'Show system tray icon',*
*'Minimize to tray instead of taskbar',*
*'Minimize to tray when clicking the main windows close button'*
[/INDENT]and optionally ..
[INDENT]*'Start minimized'.*
[/INDENT]
Now when you run it, there will be a tray icon and you just use the 'X' close button to get it out of the way. You will need to right-click on the tray icon to completely close the program.

---

### Post by Irihapeti on 2012-07-15
I can get it to minimize but it won't restore again when I click on the systray icon.

Is there something else I need to set?

---

### Post by Stray Wolf on 2012-07-16
> **wallaroo said:**
> You need to go to 'Extras -> Settings' and tick .. [INDENT]*'Show system tray icon',*
*'Minimize to tray instead of taskbar',*
*'Minimize to tray when clicking the main windows close button'*
[/INDENT]and optionally ..[INDENT]*'Start minimized'.*
[/INDENT]Now when you run it, there will be a tray icon and you just use the 'X' close button to get it out of the way. You will need to right-click on the tray icon to completely close the program.

I'm sorry I should have been more specific. Those options are there, but gray and not selectable. Thanks for the response though!

---

### Post by Irihapeti on 2012-07-16
I've discovered that there's a bug report about this. [https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/992582](https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/992582)

I'm using Gnome-fallback, which behaves differently from Unity. I noted the same greyed-out behaviour in Unity myself.

See [https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/842224/comments/6](https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/842224/comments/6) for further info. Looks like it's by design.

On my EeePC with Openbox and Tint2, restore from systray works correctly.

I haven't tried any workarounds for Gnome-panel yet.

---

### Post by Stray Wolf on 2012-07-16
> **Irihapeti said:**
> I've discovered that there's a bug report about this. [https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/992582](https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/992582)

This solution looked plausible:
the easiest workaround in the mean time is to add the following to ~/.config/sni-qt.conf:
 [need-activate-action]
keepassx=1
 In addition, if you have a window  that has disappeared with changes to the file, and you need to recover  it, select "Quit" from the menu, then "Cancel" when asked if you want to  save changes - this will restore the window.


...then I saw that I have no sni-qt.conf. :*(


> **Irihapeti said:**
> I'm using Gnome-fallback, which behaves differently from Unity. I noted the same greyed-out behaviour in Unity myself.

See [https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/842224/comments/6](https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/842224/comments/6) for further info. Looks like it's by design.

On my EeePC with Openbox and Tint2, restore from systray works correctly.

I haven't tried any workarounds for Gnome-panel yet.

Thanks for the help!

---

### Post by Irihapeti on 2012-07-16
> **Stray Wolf said:**
> This solution looked plausible:
the easiest workaround in the mean time is to add the following to ~/.config/sni-qt.conf:
 [need-activate-action]
keepassx=1
 In addition, if you have a window  that has disappeared with changes to the file, and you need to recover  it, select "Quit" from the menu, then "Cancel" when asked if you want to  save changes - this will restore the window.


...then I saw that I have no sni-qt.conf. :*(



Maybe it applies to when compiling from source, but that's only a guess on my part.

---

### Post by Irihapeti on 2012-07-16
It turns out that there's a file sni-qt.conf in /etc/xdg

You can edit that one, or, probably better, create a file called sni-qt.conf in your .config directory and add:
```
[need-activate-action]
keepassx=1

```

That makes it work in Gnome-panel. To restore from minimized, you need to left-click on the icon and choose "activate".

It's still greyed out in Unity, though. I've heard of people installing the tint2 taskbar in Unity and locating it at the bottom of the screen. I've not tried that, though.

---

### Post by Stray Wolf on 2012-07-19
Despite the inconvenience of it's operation I like keepassx. Makes me feel a lot more secure about my accounts. But, I hope this inconvenience is overcome.

---

### Post by Irihapeti on 2012-07-19
I agree. I've just changed over my password management to KeePassX - partly as a result of this thread. There's also a version for smartphones, Keepassj2me. The data files are completely compatible, which is very convenient.

---

### Post by Stray Wolf on 2013-05-31
I finally have keepassx working the way I want with Ubuntu 12.04! I followed these instructions [http://www.keepassx.org/forum/viewtopic.php?f=4&t=2448#p4552](http://www.keepassx.org/forum/viewtopic.php?f=4&t=2448#p4552) and got additional help here: [http://askubuntu.com/questions/302185/instructions-to-add-context-menu-option-to-keepassx-indicator-applet-needs-dumbe](http://askubuntu.com/questions/302185/instructions-to-add-context-menu-option-to-keepassx-indicator-applet-needs-dumbe). Enjoy!

---

