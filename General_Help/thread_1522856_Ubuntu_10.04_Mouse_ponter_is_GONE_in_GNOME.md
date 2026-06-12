---
title: "Ubuntu 10.04: Mouse ponter is GONE in GNOME"
date: 2010-07-02
forum: General Help
---

### Post by jrop on 2010-07-02
This is what I did:
System->Preferences->Monitors
Then I changed to a higher resolution, and after clicking apply, the mouse pointer disappears.

Now for the really weird part.  If I open up a terminal and do stuff, and then type "exit", the pointer shows again.

???

What in the world?-- and how do I get it back permanently?

This is REALLY irritating.

---

### Post by jrop on 2010-07-02
Hmm, well I figured out the weird terminal behavior.  When you start typing in the terminal it hides the mouse.  Once the mouse is moved after typing in the terminal, or the terminal is closed, the mouse is shown again.

It seems like the mouse isn't shown by default upon login.

Here is my Xorg log.

---

### Post by Xalorplex on 2010-08-09
jrop, I just installed 10.04 last weekend (read: VERY new to Ubuntu) and one of the first things I noticed was that I was having the same issue as you.  I increased the resolution of my monitor and the mouse seemed to disappear.  It didn't freeze because I could still use it to navigate menus and such, but no graphic for the cursor would show.  I found that if I clicked "Apply" a second time (keeping the same increased resolution) the cursor would return.  

This is only a temporary fix though because once rebooted, the cursor disappears again and I have to do the "apply" trick again.  I'm still looking for a more permanent fix though.  Let me know if you found one!

---

### Post by jrop on 2010-08-09
Unfortunately, the computer that this was happening on isn't working anymore, so I was never able to sort this out.  I am very curious what the solution is to this problem.

In my experience, Ubuntu has gone downhill since version 9.04, as it seems that the Ubuntu developers are too eager to add too many new features to each release.  The newer versions run on some of my computers (and when it runs, it's fantastic), but not all, whereas Jaunty (9.04) runs on all of them with no problem.  I really love Ubuntu and don't want to switch to another distribution, so I'm hanging in there to see if these issues get sorted out.

---

