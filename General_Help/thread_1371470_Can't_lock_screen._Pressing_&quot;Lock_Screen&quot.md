---
title: "Can't lock screen. Pressing &quot;Lock Screen&quot; does nothing."
date: 2010-01-03
forum: General Help
---

### Post by Svens on 2010-01-03
Hello eveybody!

I have experienced that the button in my main menu "Lock Screen" does nothing, so I can not lock my screen. What could be the problem?
Is there any command in terminal what I could write, so I can see is there an error output or something?
I am using Ubuntu 9.10, GNOME.
Thank You!

---

### Post by warfacegod on 2010-01-03
Try this:

Right click any Panel and select Add to Panel. Scroll down until you find lock screen, highlight it and click add button.

Hit that new icon and see if it works.

---

### Post by Barriehie on 2010-01-03
From the terminal:
```

gnome-screensaver-command -l
```

---

### Post by s.fox on 2010-01-03
Hi,

I remember reading about this before.  If memory serves it is related to the screen saver being disabled. Is it currently disabled? If so try enabling it.

Hope this helps

-Silver Fox

---

### Post by Svens on 2010-01-03
Thank You for your all replies!
But unfortunately the lock screen adding to panel does not work too.
And if I give the command 
```
gnome-screensaver-command -l
```
it says, that my screensaver is not running. But it is not true - my screensaver IS running. What could be the problem?

I added a picture, so you can be sure that screensaver ir running, but in terminal output it is said, that it is not running.

---

### Post by Svens on 2010-01-03
Oh, how stupid can I get? :D
Somehow, there was no gnome-screensaver service started along with system start, so I checked the sessions that are started along with system start, and yes - screensaver was not checked. Now, that it is checked, everything works fine!
Thank you all, and I am sorry for wasting your time on such a "problem".

---

