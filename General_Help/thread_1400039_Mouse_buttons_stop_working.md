---
title: "Mouse buttons stop working"
date: 2010-02-06
forum: General Help
---

### Post by jcobban on 2010-02-06
I am running 9.10 (Karmic) on a Compaq Presario CQ60 laptop with Nvidia graphics.  I have installed the -185 driver which has solved most problems.  However every so often the system seems to lose track of the mouse button state.  The first symptom of this is that all mouse movements on text are treated as if the left button is being held down: mouse movement selects text rather than just moving the graphics cursor.  I am using a M$ optical mouse.

I have tried:
[LIST=1]
[*]unplugging and replugging the mouse
[*]using Ctl-Alt-F1 to go into a console and Ctl-Alt-F7 to go back to the GUI
[/LIST]

I am able to shut down all of the open windows normally using the keyboard, but the only way I have so far found to get the GUI working again is to reboot the system.

Can anyone suggest a less drastic recovery?

---

### Post by jcobban on 2010-02-06
I have activated the Ctl-Alt-Bspace key sequence to restart X.

---

### Post by dcstar on 2010-02-07
> **jcobban said:**
> I am running 9.10 (Karmic) on a Compaq Presario CQ60 laptop with Nvidia graphics.  I have installed the -185 driver which has solved most problems.  However every so often the system seems to lose track of the mouse button state.  The first symptom of this is that all mouse movements on text are treated as if the left button is being held down: mouse movement selects text rather than just moving the graphics cursor.  I am using a M$ optical mouse.
.........

There are numerous bug reports on this sort of thing going back years now, and it seems to affect Nvidia systems quite a bit.

You can try and search them out if you want to add your experience to them.

---

### Post by jcobban on 2010-02-07
> **dcstar said:**
> There are numerous bug reports on this sort of thing going back years now, and it seems to affect Nvidia systems quite a bit.

You can try and search them out if you want to add your experience to them.

Thank you.  I did a search in launchpad and added a comment to the thread that seemed closest.

I now suspect that the problem is actually related to the touchpad.  As I type occasionally my fingers or the palm of my hand may brush against the touchpad.  Even though I have pressed the little button above the touch-pad that is supposed to deactivate it, I observe that "mouse" actions are still honored.  The last time my system got into the state where it thought the left mousebutton was being held down, I just thumped the touchpad, and the state changed.

---

