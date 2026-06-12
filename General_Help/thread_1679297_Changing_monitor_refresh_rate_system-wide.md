---
title: "Changing monitor refresh rate system-wide"
date: 2011-01-31
forum: General Help
---

### Post by Astnya on 2011-01-31
On an older computer of mine using an older CRT monitor, Ubuntu defaults to a monitor refresh rate that causes the screen to constantly flicker and flash, making it nearly unusable. Changing the rate to either 75 Hz or 60 Hz fixes the issue, but changing it through the Monitor settings only affects my user account; part of the loading screen, and the login screen, will continue to flicker and flash.

Is there a setting I can adjust somewhere that will set the refresh rate for the entire system, not just my user account?

---

### Post by Astnya on 2011-02-01
bump

---

### Post by Krytarik on 2011-02-01
Follow this guide to set it up, either by using xrandr at startup or by xorg.conf:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Astnya on 2011-02-01
Thanks for the link. It's helpful, though I'm stuck.

First:

> Note that changes you make using xrandr only last through the current session.So I have to [set the changes permanently]("https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20changes%20persistently"). Three methods are listed for doing this:

> Using ~/.xprofile
> Modifying a startup script in /etc/gdm/
> Editing xorg.conf

The first method will not solve my problem, as the page states that it is user-specific, and so won't affect the loading screen or the login screen.

I've tried method two by following the instructions and adding ' xrandr --rate=75 ' to /etc/gdm/Init/Default after the ' initctl -q....' bit as root. However, I logged out and the login screen continued to flicker and flash. Is logging out not good enough, or is there something else I have to do?

And, of course, xorg.conf is overwhelming and I wouldn't know the first thing about editing it.

---

### Post by Krytarik on 2011-02-01
You have to restart GDM to apply your change to it:

- logout
- press Alt+Ctrl+F1
- login at the console
```

sudo service gdm stop
sudo service gdm start
```However, I believe it's necesserary to also pass the output port, like this:
```
xrandr --output VGA1 --mode 1024x768 --rate 75
```You should check before, if this mode is even available, and what your output port is:
```
xrandr
```And then check if your command works by also entering it in the terminal. If it works there, it should also work at (GDM's) startup.

---

### Post by Astnya on 2011-02-01
> **Krytarik said:**
> You have to restart GDM to apply your change to it:

- logout
- press Alt+Ctrl+F1
- login at the console
```

sudo service gdm stop
sudo service gdm start
```

This, combined with fixing a stupid typo (using --rate 75 instead of --rate=75) appears to have solved the problem. Thank you very much. =)

> However, I believe it's necesserary to also pass the output port, like this:
```
xrandr --output VGA1 --mode 1024x768 --rate 75
```As it turns out, I did not have to do this. xrandr --rate 75 alone takes care of it.

---

### Post by Krytarik on 2011-02-01
> **Astnya said:**
> This, combined with fixing a stupid typo (using --rate 75 instead of --rate=75) appears to have solved the problem. Thank you very much. =)
Oh, I didn't notice that at the first sight.
> **Astnya said:**
>  As it turns out, I did not have to do this. xrandr --rate 75 alone takes care of it. Thanks for the feedback, maybe because there is only one monitor at your machine, or it always takes the first output port if not specified otherwise.

Then please mark this thread as "solved", via "Thread Tools".

---

