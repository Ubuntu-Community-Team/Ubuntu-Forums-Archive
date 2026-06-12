---
title: "LaTeX with Gedit: what is this error?"
date: 2009-07-05
forum: General Help
---

### Post by pooja on 2009-07-05
When I compile a .tex file from *Tools > Latex2PDF* I get this error (see attached picture) in the panel at the bottom of Gedit's window. What does it mean and how do I fix this problem?

---

### Post by hugmenot on 2009-07-05
This is a [known bug]("https://bugs.edge.launchpad.net/ubuntu/+source/rubber/+bug/338285") that is mostly cosmetical because it is only a warning. 

If you want to get rid of it you have to make a two line change in a file belonging to the rubber package. Details in the bug report.

---

### Post by pooja on 2009-07-06
I've visited the link and have seen the DIY patch but don't know what to do next. Do I have to copy it in the terminal and press ENTER? What to do next?
Can you tell me step by step what to do?
Thanks.

---

### Post by ad_267 on 2009-07-06
See post number five on that page. You have to edit the util.py file.

You can run "gksu gedit /usr/share/rubber/rubber/util.py" by pressing alt-f2 or from a terminal if you like.

---

### Post by pooja on 2009-07-06
Thank you so much for your help!

---

