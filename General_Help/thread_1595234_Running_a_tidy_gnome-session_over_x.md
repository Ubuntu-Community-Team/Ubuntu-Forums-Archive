---
title: "Running a tidy gnome-session over x"
date: 2010-10-13
forum: General Help
---

### Post by zugvogel on 2010-10-13
Hello,
Can anyone help me tidy up my remote gnome-session?

I have both a mac and ubuntu box sitting on my desk. I work on the mac and access the ubuntu box over ssh.
Often I need the point-and-click interface of the ubuntu box, at which point I run gnome-session.
The problem is that the top and bottom menu bars fill the full size available to them, which can cause me problems (I use two different-sized screens and the bars get hidden), and overall it looks very messy.

I would therefore like to confine the gnome-session to a window, much like you get with vnc (or parallels if you're running a virtual ubuntu session).

Is this possible in any way?

Thanks!

---

### Post by zugvogel on 2010-10-15
Is there really no way to do this?

---

### Post by roggenschrotbrot on 2010-10-15
can't give you a solution, but maybe Xephyr could be of use.

---

### Post by zugvogel on 2010-10-17
Hi RSB,

Thanks for your help.
Your suggestion led me to Xnest, and I've made a step forward, but still have not managed to get it working.

I installed Xnest via apt-get, and then run the following command:

Xnest :30 -geometry 800x600 -query localhost &

This brings up a black box.

I then tried:
gnome-session --display :30

but it says "** (gnome-session:10340): WARNING **: Cannot open display: :30"

I tried a couple of varients on this theme but without success. Can anyone help me further?

Thanks!

---

### Post by zugvogel on 2010-10-18
I'm sure it's just a problem of somehow specifying the correct display - does anyone know how to get this working?

---

### Post by zugvogel on 2010-10-21
anyone?

---

