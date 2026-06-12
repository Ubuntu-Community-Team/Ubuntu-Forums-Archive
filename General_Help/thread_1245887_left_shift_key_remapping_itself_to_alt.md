---
title: "left shift key remapping itself to alt?"
date: 2009-08-21
forum: General Help
---

### Post by TotallyLuckless on 2009-08-21
i am trying to narrow down the source of this problem, which is hopefully just software and the reason why i'm starting here.

during normal usage of my system, open office, pidgin, a terminal with python, and firefox, the left shift key suddenly ceased functioning. (i think i first noticed it using facebook chat.) rather than functioning as shift it gave the same results as alt.

the hardware is a standard ASUS Eee pc 900, and it is running Ubuntu 8.04.

one 'fix' i have found is to completely power down the system, with power and battery pulled. i don't know if it was the extreme of pulling the battery, or just a full shut down, but a simple restart from the menu did not seem to have an effect. however the error returned shortly after. i'll be doing more tests shortly.

given the position of the right shift key on this keyboard, it makes typing and trying to quickly narrow down searches less than easy.

thank you for any help you may have in narrowing down this problem. i really don't want to load up xandros or whatever it was called again to test if it is hardware related or not.

---

### Post by TotallyLuckless on 2009-08-21
Update: The problem seems to have cleared itself, for now.

However this makes me even more worried about this error, given that classes are about to start again soon and I use this laptop for a lot of papers.

---

### Post by aldimond on 2009-08-21
The first thing I'd check is xmodmap.  Open a terminal, run "xmodmap", and post the output here.  It also might be helpful to see the X events, so you might try running xev from a terminal.  A small window will pop up.  You can give the window focus, then hold the left shift key, type a letter, release the left shift key, close the xev window.  A bunch of output should be in the terminal... find the stuff related to keyboard events and modifier state and post it here.  If you have this problem again do the same tests while the problem is occurring and post the results.  I'll follow the thread and take a look at what you post.

Other useful data points: when the problem is occurring hit ctrl+alt+f2 to get to a real terminal outside of X.  Does the problem exist there as well?  (usually ctrl+alt+f7 will get you back to your desktop... if not, try ctrl+alt+f-keys until one takes you back).

---

