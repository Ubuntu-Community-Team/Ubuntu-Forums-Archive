---
title: "How to change Default Desktop Name"
date: 2012-09-12
forum: General Help
---

### Post by Hazzabin on 2012-09-12
G'day
Is there a simple easy way of changing the default desktop name 'Ubuntu Desktop' to XYZ, I am currently running Ubuntu 12.04.

regards
Hazz

---

### Post by opensshd on 2012-09-12
You can, it involves recompiling your window manager to do it though, as far as I know.

That is, if you are talking about the one in the top panel in Unity? I looked into customizing it - it involves altering source code - hence, recompiling.

---

### Post by Hazzabin on 2012-09-12
> **opensshd said:**
> You can, it involves recompiling your window manager to do it though, as far as I know.

That is, if you are talking about the one in the top panel in Unity? I looked into customizing it - it involves altering source code - hence, recompiling.

Yes mate it was what I was referring to, damn'tt lol, was hoping for an easier way, as I'm not all that smart.

Thanks for your reply

---

### Post by opensshd on 2012-09-12
No problem, please marked as solved in thread tools menu :)

---

### Post by MG&amp;TL on 2012-09-12
> **opensshd said:**
> You can, it involves recompiling your window manager to do it though, as far as I know.

That is, if you are talking about the one in the top panel in Unity? I looked into customizing it - it involves altering source code - hence, recompiling.

If you could find the binary the "Ubuntu desktop" string belongs to, you could simply **carefully** edit that binary in-place, negating the compiling step. The *strings  *command should be very helpful should you take that path.

PS *Strings are stored as plaintext in binaries, no need to learn binary first.  *:)

---

### Post by opensshd on 2012-09-12
> **MG&TL said:**
> If you could find the binary the "Ubuntu desktop" string belongs to, you could simply **carefully** edit that binary in-place, negating the compiling step. The *strings  *command should be very helpful should you take that path.

^ Nice


Found from: 

[http://askubuntu.com/questions/140742/how-do-i-change-the-desktop-name-on-the-unity-panel](http://askubuntu.com/questions/140742/how-do-i-change-the-desktop-name-on-the-unity-panel)

Currently in unity-5.12 would be found in /plugins/unityshell/src/PanelMenuView.cpp, line 78

 _desktop_name(_("Ubuntu Desktop"))
In unity-2d, unity-2d 5.12, /panel/applets/appname/appnameapplet.cpp line 369

---

### Post by Hazzabin on 2012-09-12
thanks guys for your answers very much appreciated, now to find how to mark 'Solved'ok done it

---

### Post by MG&amp;TL on 2012-09-12
> **Hazzabin said:**
> thanks guys for your answers very much appreciated, now to find how to mark 'Solved'

Thread tools (second bar down at the top)->Mark as solved. 

:)

---

