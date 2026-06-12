---
title: "Unity2D &amp; Global Menu"
date: 2011-10-26
forum: General Help
---

### Post by KoopaTroopa on 2011-10-26
Hello!

So I've uninstalled the global menu and now when a window is not maximised it gives me back the title bar with the close, minimise and maximise buttons.

[http://i53.tinypic.com/o8xld2.png]("http://i53.tinypic.com/o8xld2.png")

However (with the exception of Chrome) when a window is maximised then the close, minimise etc buttons once again revert back to hiding away in the top left hand corner.

[http://i52.tinypic.com/9v8bpz.png](http://i52.tinypic.com/9v8bpz.png)

How can I have the title bar with the close etc buttons on show and attached to the window when it's maximised or not.

---

### Post by woodyg on 2011-10-27
Same problem here. I just installed Ubuntu 11.10 and am now trying to remove all those annoying "features" that is to be found in Ubuntu nowadays... global menu, overlay scrollbars, hiding launcher, missing taskbar... 

Anyone got a solution?

---

### Post by Vaphell on 2011-10-27
launcher bar is the taskbar - it works just like in win7. icon that is there acts as a launcher when there are 0 instances and as a taskbar group when there are 1+

global menu
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```
overlay scrollbars
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```
always visible launcher bar
```
sudo apt-get install dconf-tools
dconf write /com/canonical/unity-2d/launcher/use-strut true
```

---

### Post by woodyg on 2011-10-27
> **Vaphell said:**
> launcher bar is the taskbar - it works just like in win7. icon that is there acts as a launcher when there are 0 instances and as a taskbar group when there are 1+


Do not quite understand... but I think xfce4-panel should do the trick. Will try later...

> **Vaphell said:**
> 
global menu
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```

Works, but the problem is that when a window is maximised then the close, minimise etc buttons once  again revert back to hiding away in the top left hand corner.

> **Vaphell said:**
> 
overlay scrollbars
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

I did this, and it works for most common applications, but not all... e.g. grub customizer still use those overlay scrollbars. Is it possible to remove from all applications, or is it hardcoded into some of them?

> **Vaphell said:**
> 
always visible launcher bar
```
sudo apt-get install dconf-tools
dconf write /com/canonical/unity-2d/launcher/use-strut true
```

hide_mode=0 and use_strut is ticked... still the launcher is hiding whenever any application is visible (launcher is visible if all applications are minimised though). Ideas? (remember, **this is 2D**)

---

### Post by KoopaTroopa on 2011-10-27
> **Vaphell said:**
> launcher bar is the taskbar - it works just like in win7. icon that is there acts as a launcher when there are 0 instances and as a taskbar group when there are 1+

global menu
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```
overlay scrollbars
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```
always visible launcher bar
```
sudo apt-get install dconf-tools
dconf write /com/canonical/unity-2d/launcher/use-strut true
```

But this still doesn't answer my question about the close minimise etc buttons hiding away in the top left when a window is maximised?

---

### Post by Vaphell on 2011-10-27
> But this still doesn't answer my question about the close minimise etc buttons hiding away in the top left when a window is maximised?

sorry, afaik that's the way of unity. Yes, it sucks, no, nothing can be done about it at the moment (if ever). Shop around for another DE that will suit your needs.

> hide_mode=0 and use_strut is ticked... still the launcher is hiding whenever any application is visible (launcher is visible if all applications are minimised though). Ideas? (remember, this is 2D)

i remember, unity in 3d flavor is configured via compiz plugin in ccsm. My netbook is configured like that and launcher definitely doesn't hide. Logout/login, restart?

---

### Post by woodyg on 2011-10-27
I am sooo close to moving to Xubuntu... if only it didn't look so unpolished. Makes one think of Windows95 or something similar.

---

