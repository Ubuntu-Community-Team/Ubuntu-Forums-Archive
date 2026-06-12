---
title: "'places' opens in video player"
date: 2009-11-23
forum: General Help
---

### Post by ZorgTheDestroyer on 2009-11-23
I have experienced a curious problem after installing 9.10 on my secondary computer. When I go to 'Places - any folder' it opens in a videoplayer. It's not a big problem, I just put a shortcut on my desktop to my homefolder, and it works. However I would like to find a way to make it open in a window instead. I'm not very experienced with computers, so there may be something obvious I should do. Please help.

---

### Post by prshah on 2009-11-23
> **ZorgTheDestroyer said:**
> to 'Places - any folder' it opens in a videoplayer. 

This is a known bug. Open "Computer" from the Places location, (or just run nautilus from the Alt+F2 "command" box). Now, navigate to your home directory, then right click any directory within it, and choose "Open With"-"Open with other application"; in the box that pops up, choose "File Browser".

From now on, it will open correctly.

Here's another way you can try; System-Preferences-File Management. If you can't find that option, press Alt+F2, and run ```
nautilus-file-management-properties
```

Then click the Behaviour tab, and select the option "Always open in browser windows", then click Close.

Now perform the earlier method again, and see if it "sticks"

If that doesn't work as well, right click any directory in your home directory, then choose Properties-Open With-File Browser-Close. If the "File Browser" option is not there, click on Add and locate "File Browser". If you still cannot find the option, at the bottom of the "Add Application" window, click on "Use a custom command" and give the command as ```
nautilus
```.

---

