---
title: "Dual monitor problems,UB 8.10 x64"
date: 2009-06-26
forum: General Help
---

### Post by muad on 2009-06-26
Ok. First, I did google, and found a wealth of information. However, it was all for using twinview, and I don't think that is what I am wanting. 

When using one monitor, at the bottom right I have access to two desktops (I can also rotate my mouse wheel to switch between them). I want to have one active desktop on one monitor, and that second desktop on the secondary monitor. 

My main monitor is a Dell 24-inch wide display. The secondary monitor is a Dell 17-inch display. Here is my video card specs, and it has dual AVI output:

nVidia G71 (GeForce 7900 GS)

I don't nessasarly need to be able to drag a window over, I just want to be able to move my mouse cursor from one screen to the other, then open whatever programs, etc. inside the opposite monitor. When I got twinview working, it looked like one huge merged display. 

Any help is greatly appreciated!

:popcorn:

---

### Post by muad on 2009-06-26
FWIW, I have twinview working, and I am able to use the secondary display by dragging a window over. It's usable, but still not what I had in mind.

---

### Post by Grenage on 2009-06-26
Can you not simply deselect Twinview and use them as separate desktops?

---

### Post by muad on 2009-06-26
Well, the options are disabled, separate X screen (can't get to work), or twinview (works).

---

### Post by Grenage on 2009-06-27
Separate X screen is what you want, so it will be worth your time dabbling with that.

---

### Post by muad on 2009-06-29
> **Grenage said:**
> Separate X screen is what you want, so it will be worth your time dabbling with that.

Thanks for the heads up.

---

### Post by Grenage on 2009-06-30
No worries; if you get any specific error messages or problems then let us know here.

It's often worth rebooting (or at least restarting X) after saving the changes to xorg.conf.  A lot of the time I found that a particular setting didn't work until I rebooted.

---

