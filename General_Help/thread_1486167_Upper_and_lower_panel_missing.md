---
title: "Upper and lower panel missing"
date: 2010-05-17
forum: General Help
---

### Post by rmcellig on 2010-05-17
For some reason when I restarted my computer today, I see the desktop but my panels are missing. What should I do? I am running Xubuntu 10.04

---

### Post by TheStroj on 2010-05-17
simply run "gnome-panel" from terminal...im not sure if this is what you are looking for but i guess it should be.

---

### Post by SlidingHorn on 2010-05-17
> **TheStroj said:**
> simply run "gnome-panel" from terminal...im not sure if this is what you are looking for but i guess it should be.

Chances are, if you have no panel, you don't have a menu...to start your terminal without a menu, right-click anywhere on your desktop & select "Create Launcher".  In the command field, type:

```
terminal
```

Double click the launcher & type into your terminal:

```
gnome-panel
```

Be sure to save your session and you should be all set.

---

### Post by TheStroj on 2010-05-17
you can also use alt+f2 and run gnome-terminal or xterm or whatever you use(xterm should always work)

---

### Post by SlidingHorn on 2010-05-17
> **TheStroj said:**
> you can also use alt+f2 and run gnome-terminal or xterm or whatever you use(xterm should always work)

...or you can take the easy, cheater's way like he said ;)  j/k

---

### Post by rmcellig on 2010-05-17
Thanks! I will try that out. So the panels I had before are gone for good now, or will they return when I type in gnome-panel?

---

### Post by TheStroj on 2010-05-17
well they should come back :P
if they dont, let us know

---

### Post by SlidingHorn on 2010-05-17
I'm not entirely sure to be honest...hopefully gnome-panel will remember what settings you had previously

---

### Post by rmcellig on 2010-05-17
Thanks again!! Do you know what would cause the panels to disappear?

---

### Post by TheStroj on 2010-05-17
i dont know how could i miss the thread was [xubuntu] XD

well, just replace the word "gnome" with "xfce" i guess :P

---

### Post by SlidingHorn on 2010-05-17
> **TheStroj said:**
> i dont know how could i miss the thread was [xubuntu] XD

well, just replace the word "gnome" with "xfce" i guess :P

Nice catch...totally  missed that

---

### Post by rmcellig on 2010-05-17
how do I save the session once I put gnome-panel in the terminal window?

---

### Post by TheStroj on 2010-05-17
Read this, seems like a common bug:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/53897](https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/53897)

---

### Post by SlidingHorn on 2010-05-17
> **rmcellig said:**
> how do I save the session once I put gnome-panel in the terminal window?

well first off, if you're running xubuntu, use "xfce-panel" instead of "gnome-panel"

to save the session, just type into your terminal:

```
xfce-session-save
```

---

### Post by rmcellig on 2010-05-17
Thanks!! So far so good...

---

### Post by XubuRoxMySox on 2010-05-17
*Right*-click anywhere on the desktop, choose **Applications > Settings > Xfce4 Settings Manager**. From there select Panels, add one or multiple panels as you see fit. From the Xfce4 Settings Manager you can save all your settings as well.

Loving my Xubuntu,
Robin

---

### Post by rmcellig on 2010-05-17
Thanks Robin! Glad to hear that you like Xubuntu. I just started using it as well.

---

### Post by rmcellig on 2010-05-18
Hi Robin,

I know this has nothing to do with my post but I was wondering how you like Xubuntu and what cool things you are doing. I am mainly a Mac user as well as Windows user using XP. I am pretty new to all this Xubuntu stuff. So much out there!! My computer is from around 2002 so Xubuntu works pretty good on it.

---

