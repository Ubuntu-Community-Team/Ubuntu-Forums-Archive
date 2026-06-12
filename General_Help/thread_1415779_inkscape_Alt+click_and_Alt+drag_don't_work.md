---
title: "inkscape: Alt+click and Alt+drag don't work"
date: 2010-02-25
forum: General Help
---

### Post by hanzj on 2010-02-25
In Ubuntu, 

Alt+Drag (a.k.a Alt+ClickDrag) is defaultly set-up for moving windows.

But in Inkscape, Alt+Drag is used for something called Select Under. The tutorial page says the following > 
What to do if the object you need is hidden behind another object? You may still see the bottom object if the top one is (partially) transparent, but clicking on it will select the top object, not the one you need. 

This is what Alt+click is for. First Alt+click selects the top object just like the regular click. However, the next Alt+click at the same point will select the object below the top one; the next one, the object still lower, etc. Thus, several Alt+clicks in a row will cycle, top-to-bottom, through the entire z-order stack of objects at the click point. When the bottom object is reached, next Alt+click will, naturally, again select the topmost object[http://www.inkscape.org/archive.php?year=2004&month=09](http://www.inkscape.org/archive.php?year=2004&month=09) says
> On Linux you may have to disable dragging the window with Alt if you want to use this. Even though I've changed the "moving windows" function to 
> Super (or "Windows Logo") by going to System/Windows, Alt+Click still doesn't work in Inkscape to "Select Under".

Please advise.


[COLOR=DimGray](Note: This post is almost the same as my posting of a year-2006 now-locked/archived thread [http://ubuntuforums.org/showthread.php?t=170735](http://ubuntuforums.org/showthread.php?t=170735) )[/COLOR]

---

### Post by hanzj on 2010-02-25
Solved!

My keyboard/language switcher (um, i don't remember the name) was getting in the way. When I made it quit, the Alt in Inkscape works just fine (can do "select under").

---

