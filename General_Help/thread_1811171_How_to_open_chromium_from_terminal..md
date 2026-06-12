---
title: "How to open chromium from terminal."
date: 2011-07-24
forum: General Help
---

### Post by deckerry on 2011-07-24
In a terminal type this: ```
'chromium-browser'
```

I looked all over the internet on how to figure this out and I couldn't find it.

How did I figure it out?
I'm running Xubuntu 10.04 and it doesn't seem to let you just drag and drop the shortcut into a panel from the applications menu. You have to add the panel shortcut manually. To do this, right-click a panel and select Add New Items > Launcher. Then right-click the launcher click properties...

Here's where I got stuck. To make a good launcher/shortcut you need to know the command and put in an icon. I couldn't find the command at first so I put in the icon first instead by clicking on the icon icon (not a typo) in the launcher's properties. Select All Icons from the drop-down menu at the top of the icon selection window. Arbitrarily click on any icon and type chromium. Here's where you find your chromium icon and guess what the name of it is? "chromium-browser" This is how I figured out what the heck the command was to open the stupid thing.

Maybe this could help find other commands if you can't find them easily on the internet. Any questions?

---

### Post by zacktu on 2011-07-24
You might think that the executable is named "chromium".  It's not, as you discovered.

On the command line type

*apropos chromium*

and the response will be "chromium-browser".  Thus, you can no type

[I]chromium-browser

which chromium-browser

man chromium-browser[/I]

or whatever.

---

### Post by IWantFroyo on 2011-07-24
Usually, putting the command for an app in will also give you its icon automatically.

It sorta works both ways.

---

### Post by deckerry on 2011-07-24
> **zacktu said:**
> You might think that the executable is named "chromium".  It's not, as you discovered.

On the command line type

*apropos chromium*

and the response will be "chromium-browser".  Thus, you can no type

[I]chromium-browser

which chromium-browser

man chromium-browser[/I]

or whatever.

Thanks Zacktu, I didn't know about the apropos command. That would have made things much more simple in the beginning. Good idea!

---

