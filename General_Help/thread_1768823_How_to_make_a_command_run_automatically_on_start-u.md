---
title: "How to make a command run automatically on start-up?"
date: 2011-05-27
forum: General Help
---

### Post by an0nimity on 2011-05-27
Hello,

I have a lenovo thinkpad laptop, and it has both touch-pad (standard build in laptop mouse) and touch-point (in the middle of the keyboard) mouse options. 

I almost invariably use the touch-point and the accompanied scroller and key-buttons.

HOWEVER, for the scroller to be recognized by ubuntu you must run two scripts as follows:

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2

Restarting the computer resets these settings, and you must re-run them each time you start up ubuntu.

I am looking to write a script that will automatically run itself (which will execute the above commands), or to permanently change these settings so that it will not be necessary to run them at each start-up.

Thanks in advance, and if there is another thread on these forums that I should move to (or even just another thread that would be a more likely place to get a response), please let me know. This seemed like the best forum (one which can certainly hold this post without violating any rules), but I may have missed something.

Thanks again,
anonymous

---

### Post by Pand5461 on 2011-05-27
System > Preferences > Startup Applications (in Lucid). Then add the commands to the list.

---

### Post by an0nimity on 2011-05-27
What is lucid? I don't have that option in my system ->  pref list..

---

### Post by an0nimity on 2011-05-27
No i lied i found it, thanks alot^^

---

### Post by rvchari on 2011-05-27
> **an0nimity said:**
> No i lied i found it, thanks alot^^

if the thread is solved, can you mark it as solved ?

it will be easier for others to trace out with similar probs as solved

---

