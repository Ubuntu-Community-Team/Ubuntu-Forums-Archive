---
title: "w3m and wordwrap"
date: 2009-12-18
forum: General Help
---

### Post by sisyphus1978 on 2009-12-18
So I solved the word wrap issues with nano ([see this thread]("http://ubuntuforums.org/showthread.php?t=1352178")) and now I am stuck with word wrap issues in w3m.

Problem: Writing an email (gmail) in w3m works fine, but it adds in spurious line breaks.

Press o for options and change editor from simple-editor (I believe a syslink) to nano. Works fine. Adds in line breaks. Change the editor to gedit (I do this over ssh, so remember -X) and it still adds in line breaks. 

The issue then seems to be that w3m is adding hard breaks to the text. 

Any ideas?

---

### Post by sisyphus1978 on 2009-12-21
The more I investigate this (and boy, have I spent some time investigating this) the more I think this is actually an issue with gmail. In fact this sentence is being written on a 40inch TV, in nano, in w3m, in screen, over ssh. And I bet it wraps okay when I submit it. If that is the case, then I might set up a terminal mail client, so I can get control of the wrapping in my emails.

---

### Post by sisyphus1978 on 2009-12-21
Consider this solved. It is apparently a problem with gmail in browser. I have set up mutt and am getting normal wrapping behaviour.

---

