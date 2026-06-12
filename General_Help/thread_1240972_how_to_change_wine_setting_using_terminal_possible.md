---
title: "how to change wine setting using terminal? possible?"
date: 2009-08-15
forum: General Help
---

### Post by rock it on 2009-08-15
Hi, I was messing about with the graphics settings for wine and I changed the font size and the screen res. now I cant view the section to change them back because the settings go of the page. Is there a way to edit the settings using the terminal or without having to use wine?

---

### Post by michy99 on 2009-08-15
I think you can edit ~/.wine/user.reg to fix it. Here's what my Console section looks like:```
[Console] 1218918217
"CursorSize"=dword:00000019
"CursorVisible"=dword:00000001
"EditionMode"=dword:00000000
"ExitOnDie"=dword:00000001
"FaceName"="Courier\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"
"FontSize"=dword:000d0008
"FontWeight"=dword:00000000
"HistoryBufferSize"=dword:00000032
"HistoryNoDup"=dword:00000000
"MenuMask"=dword:00000000
"QuickEdit"=dword:00000000
"ScreenBufferSize"=dword:00190050
"ScreenColors"=dword:0000000f
"WindowSize"=dword:00190050
```

---

### Post by rock it on 2009-08-15
[COLOR=White].[/COLOR]

---

### Post by rock it on 2009-08-15
cant find the section to edit, have tried search but hasn't found what I'm after.

---

### Post by michy99 on 2009-08-15
That [console] section is at the very beginning of my ~/.wine/user.reg file.

---

### Post by rock it on 2009-08-15
> **michy99 said:**
> That [console] section is at the very beginning of my ~/.wine/user.reg file.
I have 


WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\Colors] 1250336348

[Control Panel\\Desktop] 1250336437
"DragFullWindows"="0"
"FontSmoothing"="0"
"LowPowerActive"="0"
"MenuShowDelay"="400"
"SmoothScroll"=hex:00,00,00,00
"UserPreferenceMask"=hex:10,00,00,80

that at the start of mine

---

### Post by michy99 on 2009-08-15
Interesting. It may not have anything to do with your problem, anyway. You could try backing up the file, adding that section to it and see what happens. If it doesn't help, you can just change it back.

---

### Post by rock it on 2009-08-15
the other thing would be if its possible to grab hold of the whole window and not  just he top bar i could move the settings into view

---

### Post by michy99 on 2009-08-15
I think I have a solution. I assume you are on the Graphics tab. Press the tab key until you see that it has selected the first option (Allow Direct X ...). This will take about 5 or 6 tabs. Press tab 8 more times. This will select the screen resolution slider. Hold the left arrow key down for about 20 seconds, This will pull the slider all the way down. Press tab twice and enter.

---

### Post by rock it on 2009-08-15
its fine I managed by pressing tab and typing numbers to get it to a reasonable screen res and have changed it from there

---

### Post by rock it on 2009-08-15
thanks for ur help

---

