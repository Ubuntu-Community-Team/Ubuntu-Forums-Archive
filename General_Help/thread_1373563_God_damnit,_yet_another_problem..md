---
title: "God damnit, yet another problem."
date: 2010-01-05
forum: General Help
---

### Post by Ilmatic on 2010-01-05
[http://img686.imageshack.us/img686/1626/screenshottf.png](http://img686.imageshack.us/img686/1626/screenshottf.png)

[B]As you can see from the link provided, the xchat application (just one of all applications of course) doesn't have the bar on top that allows me to click the "x" to close the application. If I wish to close this or any other application, I have to go to the tab at the bottom of the screen and right click for a list of actions. At first, I was fine with this. Seeing as to how I needed to access terminal though, this is what I saw that set me off.

[/B][http://img686.imageshack.us/img686/8808/screenshot1jg.png](http://img686.imageshack.us/img686/8808/screenshot1jg.png)[B]

As you can see, the top part of every window is cut off and that is why the terminal looks the way it does. Solutions anyone?



[/B]

---

### Post by askreet on 2010-01-05
The window manager is responsible for displaying the window borders and buttons.  Have you modified which window manager you are using.  You could try start metacity back up by going to tty1 (LCTRL+LALT+F1), logging in an running:

```
DISPLAY=:0 metacity & 
```

---

### Post by Ilmatic on 2010-01-05
**It says no such command. What now?**

---

### Post by spcwingo on 2010-01-05
Try this one:  Press ALT+F2 to bring up a run prompt then enter this command:

```
metacity --replace
```

---

### Post by Ilmatic on 2010-01-05
**Dude...are you in the ubuntu chat room with me? Lol. Someone suggested the same thing. Unfortunately, that command failed to render any results. It just said "unable to open x server".**

---

### Post by nothingspecial on 2010-01-06
If you are running compiz, go system > preferences > compizconfig settings manager and make sure the window decoration plugin is checked.

And by the way, I always close my windows using Alt-F4 and have the window borders turned off anyway.

---

### Post by askreet on 2010-01-06
> **nothingspecial said:**
> And by the way, I always close my windows using Alt-F4 and have the window borders turned off anyway.

That's pretty ridiculous.  I close my windows with Super-Q (PekWM :P)

---

### Post by nothingspecial on 2010-01-06
> **askreet said:**
> That's pretty ridiculous.  I close my windows with Super-Q (PekWM :P)

Actually I close my windows with whatever I feel like putting in my ~/.config/openbox/rc.xml today. :-\"

---

### Post by bobcollard on 2010-01-06
> **Ilmatic said:**
> [http://img686.imageshack.us/img686/1626/screenshottf.png](http://img686.imageshack.us/img686/1626/screenshottf.png)

[B]As you can see from the link provided, the xchat application (just one of all applications of course) doesn't have the bar on top that allows me to click the "x" to close the application. If I wish to close this or any other application, I have to go to the tab at the bottom of the screen and right click for a list of actions. At first, I was fine with this. Seeing as to how I needed to access terminal though, this is what I saw that set me off.

[/B][http://img686.imageshack.us/img686/8808/screenshot1jg.png](http://img686.imageshack.us/img686/8808/screenshot1jg.png)[B]

As you can see, the top part of every window is cut off and that is why the terminal looks the way it does. Solutions anyone?



[/B]
**Try hiding your taskbar on top.  Did you set it to cover all ?**

---

