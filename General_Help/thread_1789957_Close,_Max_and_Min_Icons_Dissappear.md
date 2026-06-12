---
title: "Close, Max and Min Icons Dissappear"
date: 2011-06-24
forum: General Help
---

### Post by YankeeFan on 2011-06-24
I'm using Ubuntu 10.4.  I have searched for this, but confess I do not know the proper words or names to use to search on.  I use max, min and close, but I've heard others refer to these as "the window dressings" and "window management icons", ...  

Just to be clear, I'm referring to the icons at the top left of most windows that I use to minimize, maximize and close windows that are open on my desktop screens.

After 30 minutes or so of firing up my desktop, I find the Max, Min and Close icons disappear from the top of all my windows.  I also find that I can no longer click in the title bar of a window and drag it across my desktop or screens (I use two monitors).  Please tell me these are not features in Ubuntu 10.4.

Anyone know of a fix for this/these or if a planned fix is in the works?

I do know other ways of closing my windows and moving them, but they are not as quick and easy as the "usual ways" of - clicking or click-hold-and-drag.

I know this is really only a nuisance, but I do wonder if it is a true bug.

---

### Post by LordNeo on 2011-06-24
Press ALT+F2 then type "gconf-editor" and press enter
Browse to:
Apps->Metacity->General

In the entry "Button Layout" type:

menu:minimize,maximize,close

(the : is a left-right separator, you can reorder as you want)

---

