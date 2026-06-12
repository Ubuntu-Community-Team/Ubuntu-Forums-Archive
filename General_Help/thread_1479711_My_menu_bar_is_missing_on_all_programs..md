---
title: "My menu bar is missing on all programs."
date: 2010-05-10
forum: General Help
---

### Post by helloblaine on 2010-05-10
[http://i862.photobucket.com/albums/ab188/filmphotog/Screenshot-1.png](http://i862.photobucket.com/albums/ab188/filmphotog/Screenshot-1.png)

Here you can see my problem

Any help? I'm running the newest release of ubuuntu.

---

### Post by finlost on 2010-05-10
That is the way it is supposed to look.

Drop and drag desired programs from the Application menu to the panel.

---

### Post by helloblaine on 2010-05-10
I don't think you understand. 

I can't move the windows..
I can't minimize, maximize, or close them..

---

### Post by Ozymandias_117 on 2010-05-10
Open a terminal and try ```
KWin --replace
``` (If that doesn't work, you can try all lowercase) I believe that is the default WM in KDE. If you close the terminal it will disappear again, this is just to test and make sure that is the problem.

---

### Post by helloblaine on 2010-05-10
KWin: command not found.

---

### Post by Ozymandias_117 on 2010-05-11
Did you try the lowercase version?

---

### Post by darkstaar on 2010-05-11
In a terminal:

```
metacity --replace
```

Does that work?

---

### Post by SeanBlader on 2010-05-11
I can't help, well I might be able to if I wanted to risk duplicating your problem, but what I can help with is your terminology. What you're missing is the "title bar" not the menu bar, and it's often called chrome because it decorates your application windows.

One thing you can actually try is resetting your theme under System -> Preferences -> Appearance. See if that helps.

---

### Post by Arachan on 2010-05-11
Hello,

I have the same problem, however ```
metacity --replace
``` fixes it temporarily. How do I permanently fix it? 

Thanks,
Arachan.

---

### Post by 3rdalbum on 2010-05-11
> **Arachan said:**
> Hello,

I have the same problem, however ```
metacity --replace
``` fixes it temporarily. How do I permanently fix it? 

Thanks,
Arachan.

In System > Preferences > Appearance, set Visual Effects to None.

---

### Post by Arachan on 2010-05-11
Hello,

That does solve the problem, but how can I not have this problem and still have my visual effects? I don't want to have to run the command, turn off visual effects and turn them back on again every time I boot. 

Thanks,
Arachan.

---

### Post by philinux on 2010-05-11
Install compizconfig-settings-manager.

Then open it from sys>prefs.

Then click effects and toggle Window Decorations.

---

### Post by Ozymandias_117 on 2010-05-11
> **SeanBlader said:**
> I can't help, well I might be able to if I wanted to risk duplicating your problem, but what I can help with is your terminology. What you're missing is the "title bar" not the menu bar, and it's often called chrome because it decorates your application windows.

If you want to get really fancy, you can call it your Window Manager. :P

---

### Post by helloblaine on 2010-05-11
> **3rdalbum said:**
> In System > Preferences > Appearance, set Visual Effects to None.

This fixed it. Thank you.

---

### Post by ninefoot on 2010-05-11
I had the same problem and this fixed it for me:

[http://ubuntuforums.org/showthread.php?t=1478301](http://ubuntuforums.org/showthread.php?t=1478301)

Neil

---

