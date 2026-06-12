---
title: "Maximize, Minimize and Close Button on top+right corner missing"
date: 2010-02-21
forum: General Help
---

### Post by deepsin on 2010-02-21
Hi Folks,
I have been using Ubuntu for couple of years but haven't encountered a problem like this before. I can't minimize or close a window (any application), as the 3 buttons form the top right corner of all windows are missing. I can still close the window using "File" Menu or other ways, but its annoying. I am using Ubuntu 9.10, 64 bit.

Is this something specific to my installation or I am hallucinating :) ?

Thanks in advance...
Deep

---

### Post by NightwishFan on 2010-02-21
First off, disable desktop effects. If that works then you have a display bug with Compiz. If that is the case, perhaps upgrade your graphics drivers.

If you are not running desktop effects, then try a different theme to see if that helps. If not, perhaps a setting wiped out your window decoration buttons. By the time you reply back I can find a command to reset the decorator configuration.

---

### Post by raktarok on 2010-02-21
Just open up the gconf-editor (Alt + F2. gconf-editor) and then navigate to apps > metacity > general. Look at the entry button_layout - you should see something similar to this:

```
menu:minimize,maximize,close
```

Correct the entry if you need to. If this does not solve the problem, try changing the theme, and see if it works.

Hope this helped!

Edit: aargh!! why is my typing speed lower than that of Nightwishfan? :)

---

### Post by deepsin on 2010-02-21
Thanks for your help Nightwishfan and Raktorak.

I did as both you folks suggested, and still have the same problem. So I was messing a bit more, and tried doing "unmaximized" by right-clicking on the tab, that I get in the bottom panel, and guess what, all the 3 buttons showed up. So I maximized again, and it seem the problem is that "I think", The top bar, that shows the title, and those 3 buttons in the right hand corner for some reason, hides under the top pannel. Obviously when I un-maximize it, the bar and the buttons becomes visible.

Any thoughts on how to fix the problem?

Thanks a lot guys

---

### Post by deepsin on 2010-02-21
BTW not sure if it matters, but I was messing with netbook-remix earlier, and then decided to get rid of it. somewhere along that time frame I guess this problem appeared.. :(

---

### Post by raktarok on 2010-02-21
Me thinks removing the netbook packages may have triggered the problem...

anyway, you could try this and see if you get the buttons back for maximized windows.

Open Compiz Settings manager (from the menu, or via the ccsm command), go to Window Decoration, make sure that it is enabled, and in the decoration windows field, see that the entry is this:
```
(any) 
```

But then, if you are using a netbook, this feature should be handy, no? I actually like this feature, and I am using it in my laptop (though my laptop has a fairly big screen) You can install an applet, that places the close, minizmize and maximize buttons on the panel, and then, things should be easy enough.

Edit: To give you an idea of how useful (and elegant) this feature can be, I hereby present a screenshot of my nautilus, in its maximized glory.

---

### Post by shwyo on 2010-03-15
System > Preferences > Startup Applications

Uncheck <Maximus Window Management.>

init 6

---

### Post by shwyo on 2010-03-15
Or if you want to keep Maximus running and get the titlebar back, I believe that this will work.

gconftool-2 --set /apps/maximus/undecorate --type BOOL false

---

