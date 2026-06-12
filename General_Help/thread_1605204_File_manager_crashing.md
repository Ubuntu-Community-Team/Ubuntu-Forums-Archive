---
title: "File manager crashing"
date: 2010-10-25
forum: General Help
---

### Post by blue carrot on 2010-10-25
Hi guys, I'm running 9.10 and have recently been encountering a problem with file manager (nautilus?) crashing / freezing when I try to use it.

Things usually run fine at start up. I can open a folder or two and find a file within it and open it.

But after I've opened one or two folders, even if I have closed the windows, I try to open a folder and the file manager totally freezes. The tab for it shows in the tool bar but I cannot click on it or open it. The other thing that happens here is all of the files disappear off my desktop as well.

Then when I go to shut down the computer it gives me a message saying 'The following programs are not responding: File manager. Shut down anyway?'.

This problem is becoming a real pain as I am in the final two weeks of writing up my masters thesis so need things to be running smoothly. I hope someone here can help!

---

### Post by sikander3786 on 2010-10-25
Try to run the file manager from terminal

```
nautilus
```

Use on till it hangs/crashes and post the output. Complete removal and reinstallation from Synaptic is another option.

---

### Post by blue carrot on 2010-10-25
Thanks for the reply. I tried the terminal thing and this was the only output that was produced. Make sense at all?
> 
(nautilus:2164): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

I really need to give my whole computer a good clean out, but I will definitley wait until after the thesis is handed in to do this!

---

### Post by blue carrot on 2010-10-25
Bump

---

### Post by stoneage on 2010-10-25
Do you have images in the problematic folder(s)?
[http://ubuntuforums.org/showthread.php?t=1380964](http://ubuntuforums.org/showthread.php?t=1380964)

---

### Post by blue carrot on 2010-10-28
hi stoneage, thanks for the link, it turns out i did have some inkscape pics saved as .jpg in the folder. i deleted them and the problem has not cropped up since. now if my system can hold itself together for the next few days and then i think i need to have a serious computer clean out!

---

