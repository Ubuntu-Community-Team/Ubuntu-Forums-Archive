---
title: "nm-applet suddenly fails..."
date: 2010-07-06
forum: General Help
---

### Post by iamyohan on 2010-07-06
I'm using openbox in 10.04 on a netbook, and for the past few months it has worked wonderfully. Today, though, the power flickered. When I looked at it again, I could no longer connect (or see) any wireless networks
Upon running nm-applet in terminal i recieve a 
"DEBUG: Old state indicates that this was not a disconnect 0"

Unfortunately this netbook is the only computer I currently have to myself. I use it for school, and it is absolutely required that I can use wireless, as wired is not an option there, nor at my home.
(I am currently using a friend's laptop at my home on my usual wireless network, so the network isn't the problem)

Searching around has gotten me nothing so far, as most people with the same issue are using gnome, and seem to have a problem with the icon disappearing... My icon is there in my tint2 panel, but detects nothing.
And the network card is on.

Please help!

EDIT: I tried the rebuilding the gnome app panel thing, but it did not help. Also, I don't know if it would make a difference, but I believe I was connected to my server computer via SSH when the power flicker occurred...

---

### Post by pastalavista on 2010-07-06
Try a full shutdown with battery and power cord removed for a few minutes then reboot. If wireless isn't restored, post the output from terminal of 'iwconfig'.

---

### Post by iamyohan on 2010-07-06
Well I'll be damned. Took me longer to write the post than fix the issue. Thank you a million times over.

---

