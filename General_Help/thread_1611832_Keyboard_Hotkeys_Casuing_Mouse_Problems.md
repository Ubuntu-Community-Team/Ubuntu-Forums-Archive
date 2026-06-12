---
title: "Keyboard Hotkeys Casuing Mouse Problems"
date: 2010-11-02
forum: General Help
---

### Post by escabuchen on 2010-11-02
Hi, this is my first post in this forum so here I go... :P

I have a Microsoft Wireless Desktop 3000 (Wireless Keyboard 3000 + Wireless Mouse 5000), actually, I have two of them, one in this computer, running Ubuntu 10.10 and another one in a box running Ubuntu 10.04.
In the box running 10.04 I can perfectly use 70% of the hotkeys the keyboard has, the 30% left I guess they're not compatible, but that's not a problem.
In the one running 10.10 whenever I use a hotkey, it works, but, at the same time it "blocks" the mouse left button in the 'pressed' state. Let me be more clear, it's like I'm holding down the left click all the time and I don't ever release it. Unless I restart the system, I can't recover the left click.

Does anybody know why this happens? Or, am I the only one with this problem?

Thanks in advance for any help you may give me. :)
Greetings.

---

### Post by trevelyan on 2010-11-05
OMG! i have the exact same problem with the same hardware.
I've been looking for a solution. Does any one know anything that could shed some light into this mystery? if i press the Escape key it will release the left click but after that the button wont do anything.

---

### Post by edulimaabreu on 2010-11-13
Same Hardware, same problem here.** I posted what solve the problem **(for me).

[http://art.ubuntuforums.org/showthread.php?p=10111004#post10111004](http://art.ubuntuforums.org/showthread.php?p=10111004#post10111004)

---

### Post by blackmonk on 2010-11-25
Hi - I have the same keyboard (MS 3000 V2) and was having the same problem. I just posted a comment on another thread on the same issue, so hope I am not doubling up. 

I found a bug discussion that had a temp fix that works for me. The bug dicussion can be found at:

[https://bugs.launchpad.net/ubuntu/+s...ev/+bug/636311](https://bugs.launchpad.net/ubuntu/+s...ev/+bug/636311)

And the solution (described in the link above) was to add a PPA to the Software Sources, and then apt-get update and apt-get upgrade. When logged out and in again I found that I can now use my special keys and not lose the function of my left mouse button.

The PPA details can be found at:

[https://launchpad.net/~raof/+archive/aubergine/](https://launchpad.net/~raof/+archive/aubergine/)

---

