---
title: "Firefox Menu Bar"
date: 2011-11-17
forum: General Help
---

### Post by Ceris on 2011-11-17
I'm currently using Ubuntu 11.10, with Firefox 7.0.1. Unity is enabled, and working properly.

Since I didn't like having Firefox's menu bar stuck in the black bar at the top of the screen, I ran this command:
```
sudo apt-get remove firefox-globalmenu
```It worked as I wanted, and removed it from that bar.

So that's why, if I right-click the toolbars at the top of the Firefox UI, I can toggle the menu bar on and off and use the Firefox Button.

However, the "Alt" key is supposed to temporarily toggle that bar on and off. At least, that's how it works in Windows.

Well, it's not too surprising that it was changed in Ubuntu, so I looked around for a solution.

I went into about:config and looked for an entry that would let me change it, but searching for "alt" and "menubar" didn't turn up anything that would do it.

I tried [this add-on]("https://addons.mozilla.org/en-US/firefox/addon/customizable-shortcuts/") but the hotkey I needed wasn't in the list of options.

I went around on Google, and about all I found is that the F10 key is supposed to work instead. Unfortunately, it doesn't. When I press F10, all it does is toggle the menu at the top that has an envelope for an icon (that menu with Chat, Mail, Ubuntu One, etc.).

I tried System Settings -> Keyboard -> Shortcuts, but neither Alt nor F10 were mapped anywhere there, even though F10 is clearly being used by Ubuntu. On the other hand, Alt (by itself) is not being used anywhere, as far as I can tell.

My alt keys both work, of course, it's just that neither is toggling the menu bar.

Sorry, but this is about all I know how to do on my own, because I'm not all that fluent with Ubuntu yet. Can anyone help?

Yes, I know, there is a thread about this. However, none of the posts in that thread helped me at all. And I don't want to needlessly revive old threads, so I thought I should make a new one.

---

### Post by BillyBoa on 2011-11-17
You could pass your question to Mozilla Forums because is very specific.

[http://forums.mozillazine.org/index.php?c=4](http://forums.mozillazine.org/index.php?c=4)

In any case if you like to get rid of the Unity global menu and see again the Firefox menu in the bar, try:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

Of course will affect all the applications.

---

### Post by vasa1 on 2011-11-17
Instead of just pressing Alt, try pressing Alt+F, Alt+E, Alt+V, Alt+H, Alt+B, Alt+T or Alt+H.

---

### Post by Frogs Hair on 2011-11-17
In Firefox under  tools > add-ons > extensions , you can disable global menu integration and enable the menu bar in the browser . Restart Firefox after the extension is disabled  and right click near the top  the panel to select menu bar .

---

