---
title: "Launcher disappears along with everything else"
date: 2011-10-22
forum: General Help
---

### Post by StevenD on 2011-10-22
I just upgraded this evening to version 11.01 and was poking around with some system settings when all of a sudden the launcher disappears along with most of the menus at the top. The only menus that show up at the top left of the screen is File, Edit, View, Go, Bookmarks, Help. I can't get to anything. I can right click on the desktop but don't get anything useful. When I type any characters a little text entry item opens in the low right corner of the screen. :(

I am at a loss as to how to get everything back. I have tried to restart several times but get the same results.

sd

---

### Post by PaulInBHC on 2011-10-22
At the login screen, click the gear and select unity 2D then log on.

Did you mess with CCSM?

---

### Post by StevenD on 2011-10-22
I'm still fairly new to Ubuntu so I have no idea what CCSM is.

I did as you instructed and clicked the gear at login and selected Unity 2D. Everything comes up except the menu with the Help column in the top left corner of the screen. I wanted to use the Help but I can't find it.

Most of what I was doing last evening was looking at different wallpapers, different themes, and I installed the CompizConfig setting application so I could reduce the size of the big icons in the launcher.

sd

---

### Post by paperclip on 2011-10-22
CCSM == compiz configuration settings manager

Try this in a terminal.

```
unity --reset
```

---

### Post by StevenD on 2011-10-22
After I posted that I didn't know what CCSM was I found it in Help. So yes I did mess with it.

I am trying the unity --reset line in the Terminal. It is taking rather a long time to do anything when it gets to the line, Setting Update "run_key". It has been sitting at that line for nearly half an hour. Is that to be expected?

Thanks for the help by the way.

sd

---

