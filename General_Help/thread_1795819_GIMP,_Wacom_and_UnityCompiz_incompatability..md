---
title: "GIMP, Wacom and Unity/Compiz incompatability."
date: 2011-07-03
forum: General Help
---

### Post by ragtag on 2011-07-03
To my surprise I'm finding that I really like Unity in 11.04, but there is one small problem with it which means I have to log in to Classic No-Effects a lot of the time. :(

When working in GIMP using a Wacom pen (which I do a lot), not all the lines I draw show up. Maybe every 1 in 5 lines, just don't show up, and it's like the brush outline freezes. This becomes pretty annoying when drawing, which is why I log in standard GNOME without effects when using GIMP.

There is a minor problem that I think may be related, and that is that sometimes when I open a windows in GIMP, such as the Save or Open dialog, I won't be able to click anything in it with my pen. I then need to click the canvas in the background, and after that everything works. It seems as though the brush is stuck on the canvas, which is similar to what happens when drawing.

I've tried different compiz settings with vSync and others, but nothing that made this work. This also seems to only be a problem when using a Wacom pen, and not when using the mouse.

Has anyone here found a solution to this problem?

---

### Post by ragtag on 2011-07-03
Hmmm....I decided to try and figure this one out on my own, and I think I may have found a solution to my own problem here. :)

I tried various things, but what did the trick was going into Edit>Preferences>Windows Management in GIMP, and setting both the "Hint for toolbox" and "Hint for other docks" to "Normal window" (not Keep above or utility window). After that the problem seems to have gone away. I tried right clicking the title bar of the Toolbox and setting it to "Always on top", but that brought back the problem.

The downside is that if the toolbox is over the canvas, and you change the focus to the canvas, it will vanish behind the canvas. You can either use Alt-Tab to bring it to the front (or use easystroke gestures like I do), or simply not maximize your canvas, and leave the toolbox visible on either side of your canvas.

I did still seem to get a similar problem when using extremely large brushes (500px or more), but that might just be a delay as the machine is writing to the canvas. It also sometimes happens when drawing the second stroke after using the toolbox, but neither of these are really that problematic.

I tried removing stuff from the toolbox, such as the picture preview, undo cue and layers, to see if any of those was the cause (as they get updated when you draw), but none of that helped.

That said, I'm pretty happy with the solution and can now keep using Unity for all my work.

---

### Post by otaconisme on 2011-09-12
Tq. Finally a real solution to my wacom bamboo problem with unity. The vsync only help to reduce the frequency of missing stroke. Your tip surely help me. :)

---

### Post by metasoarous on 2011-10-24
This doesn't help with Unity any, but I seem to have discovered that Gnome Shell does not have the same issue on 11.10. So, at least that is another alternative to avoid having to choose between lack of 3d effects and lack of full tablet functionality. Your discovery is welcome news as well.

Strangely though, it seems that once I load my wacomsettings script, the issue returns. So there may be something in the xsetwacom command that is messing things up. Haven't gone back to Unity yet to see if not running that could solve the problem there or not yet (I can live with doing redo and undo on the keyboard for a while).

---

### Post by Favux on 2011-10-24
Hi metasoarous,

> Strangely though, it seems that once I load my wacomsettings script, the issue returns.  **[won't be able to click anything in it with my pen]**  So there may be something in the xsetwacom command that is messing things up. 
If you have a xsetwacom command in the script specifying the stylus tip should be "1" i.e. left click, try commenting that out:
```
#xsetwacom set "stylus device name" Button 1 1
```

---

