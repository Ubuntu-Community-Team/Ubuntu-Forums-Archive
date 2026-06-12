---
title: "automatic monitor detection"
date: 2009-11-02
forum: General Help
---

### Post by mess110 on 2009-11-02
Ok I have been looking for ways to do this. So I decided: why not make this work generic and than give it to more people. But I have a problem now.

I have nvidia card, two monitors.
1. Laptop (widescreen - 1024x800)
2. External (normal, 1280x1024, vga)

How can I use commmand line to switch between these two?

I checked /etc/X11/xorg.conf when the laptop monitor is plugged in and after that when the external is plugged in. No difference. It could have something to do with the update to karmic koala. I suspect most tutorials I found are outdated.



To make it work I thought of two ways:
1. make a program that checks every minute and switches between some preconfigured xorg.conf
2. make a startup script that checks when u open ur computer.

Didn't decide yet, but b4 I get there.. How can I switch between the monitors??? Or how can apply different xorg conf without restarting the computer or logging out and in again?

I read something about xrandr but that didn't work for me. I am pretty sure I didn't manage to use it. Also bad internet connection in campus so research is slow. How can I do this thing?

Thanks in advance

---

### Post by mess110 on 2009-11-04
bump

help please?

---

### Post by t0p on 2009-11-04
What precisely was the problem with xrandr?  That's the utility I would use if I wanted to control monitors via the command-line.

There is a graphical utility called **grandr** that has the same functionality as xrandr but which is, of course, controlled through a GUI.

---

