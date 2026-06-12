---
title: "HOW-TO: Get your clock's text vertical in xfce panel"
date: 2012-01-24
forum: General Help
---

### Post by steevven1 on 2012-01-24
Hello all,

I had NO luck searching for a solution to my problem on the Internet, but I figured out a solution and wanted to share it. I did this under Xubuntu 11.10. I am not sure if it will apply to other versions, but give it a whirl and report back!

The problem: When you use a vertical xfce panel, the clock text is still horizontal, and gets cut off if your panel isn't massively fat.

The solution: You must enable a hidden property of the clock called "rotate-vertically." To do this:
1) Go to xfce menu -> Settings -> Settings Editor.
2) Click "xfce4-panel".
3) Click "New property" (top left).
4) Make the name "/plugins/plugin-7/rotate-vertically".
5) Make the type "Boolean" and check the "Enable" box after it appears.
6) Click "Save".

Now your clock is vertical! Yay!

---

### Post by steevven1 on 2012-06-29
This does not seem to work on the newest release of Xubuntu, 12.04. It works fine on 11.10. Any ideas?

---

### Post by vasa1 on 2012-06-29
> **steevven1 said:**
> This does not seem to work on the newest release of Xubuntu, 12.04. It works fine on 11.10. Any ideas?
But won't that look odd? In any case, I'm using analog mode: that should look okay horizontal or vertical ;)

---

### Post by rai4shu2 on 2012-06-29
I think this was fixed in 4.10, though I haven't tried it. Anyone with 4.10 want to confirm this?

---

