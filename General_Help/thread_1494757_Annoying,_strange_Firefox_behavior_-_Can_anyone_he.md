---
title: "Annoying, strange Firefox behavior - Can anyone help?"
date: 2010-05-27
forum: General Help
---

### Post by zolero on 2010-05-27
Hi all.

I have got a problem with my Firefox browser today. Dunno what I've do (at least I think that don't do anything harmful, but regular websurfing/downloading) and at some point my browser went crazy. When I select a text on a webpage and right-click to copy text selection, my browser automatically opens a new empty tab beside the actual one. Doesn't matter what page is that on which I select to copy the text, it does this always.
Now my question is: how can I disable this, and have Firefox back to present me with the "Copy" context menu option by right-clickin' (and not a new tab opened)?
Thx in  advance for your helpfulness.

PS. Forgot to say, that it acts perfectly normal to right-click on a link and open in new tab, or in any case when no block (text) selection is made. It goes crazy **only when** text selecting/right-click-copying.

---

### Post by akakingess on 2010-05-27
Obviously, the first thing to check is if this happens in a new profile with nothing else done to it (no extensions, customizations, etc.) the way that I do it is to open a terminal and type in```
firefox -p
```
the -p should open the profile manager where you can create a new one and try the same within firefox under that profile and see if it still happens. If not, than you know it is a setting or something that you have done/installed to your original profile, or just a buggy profile. If the problem still occurs, than we need to investigate a little further. Let us know if you have already done this or the results after you do try it. Good luck.

---

### Post by itag on 2010-05-29
Same problem happend here recent days.
It was caused by Tab Mix Plus 0.3.8.3.
Revert the Tab Mix Plus to 0.3.8.2 can solve the problem.

---

### Post by zolero on 2010-06-11
Thanks guys. Appreciate your responses.

**itag** had right... Tab Mix Plus extension was the evil, due a bug, I guess, in the newer 0.3.8.3 version.

Problem is gone after I've switched back to 0.3.8.2 and I keep denying TMP to update when it asks that... Yeah, is just that simple.   :D   ;)

Cheers, Z.

---

