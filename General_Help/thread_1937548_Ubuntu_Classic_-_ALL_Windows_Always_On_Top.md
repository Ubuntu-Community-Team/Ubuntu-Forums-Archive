---
title: "Ubuntu Classic - ALL Windows Always On Top"
date: 2012-03-08
forum: General Help
---

### Post by karlski on 2012-03-08
Hi, 

_OS:_  Ubuntu 11.04 logged in using Ubuntu Classic

_Problem:_  When we open apps, the new windows invariably stay hidden down in the lower tray/bar/whatever, and we have to right click "Always On Top" just to see them.  This gets annoying when you have 20 windows open and have to right click and select Always on top just to see them.  
[U]
Question:[/U]*  Is there an interface where I can set the windows to behave in the normal manner, e.g. all windows _always visible without the need to right click_?*[U]

I know, but:[/U]  Yeah it's a pretty basic question, and I am a systems engineer by trade, but after some google searches the problem is that all the posts talk about how to *enable* the vaunted "Always On Top" *feature* LOL.  

Rather than travel to a reverse parallel dimension and Google for the solution there on how to get some natural window behavior, I decided to pay the forum in this dimension a visit and ask for help.

I looked for the Compiz GUI but see none. Yet he system indicates it installed. Fascinating eh?

-k4rlski

---

### Post by jerrrys on 2012-03-08
If I understand your post, this is not normal behavior and I wonder if compiz is to blame.  A couple of things to try [in terminal.]("https://help.ubuntu.com/community/UsingTheTerminal")

[http://ubuntuforums.org/showpost.php?p=11392420&postcount=3](http://ubuntuforums.org/showpost.php?p=11392420&postcount=3)

And if that will do nothing, try:

metacity --replace

To go back to compiz enter:

compiz --replace

---

