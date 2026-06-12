---
title: "Issue with 11.04 and x11vnc"
date: 2011-05-22
forum: General Help
---

### Post by Ouroborus777 on 2011-05-22
I upgraded my 10.10 installation to 11.04. (I wish I had know it was beta before doing this. I don't like Unity (while pretty, it makes everything harder to do) and had to fix or reinstall some other things.) This is installed in a VirtualBox VM. 

With VirtualBox's 3D acceleration enabled, vnc sessions (x11vnc) do not update the graphics. They seem to be working as far as mouse and keyboard are concerned, just no graphics beyond the default backdrop. Disabling VirtualBox's 3D acceleration seems to fix this. (I tried the x11vnc flag -noxdamage to no effect.) (Another solution that seemed plausible was turning off desktop effects. The option isn't under System > Preferences > Appearance. From what I've read, the option has been removed in 11.04)

I don't remember if this was a problem for me in 10.04 and 10.10. I had 3D acceleration turned off previously and was only messing with it to see what Unity looked like.

This seems a lot like vnc/nvidia bug but none of the solutions for that are working in my case.

Is there solution for this that allows 3D acceleration to be enabled? I get the feeling that it isn't so much a 3D issue but rather that disabling 3D acceleration is having the side-effect of turning off some things in Ubuntu that are the actual problem.

At this point I don't really know what I'm doing and I can't seem to get a good solution via Google.

---

### Post by krunge on 2011-05-22
There is a thread started here on this where the poster has documented some of the problems:

[INDENT][http://ubuntuforums.org/showthread.php?t=1754078](http://ubuntuforums.org/showthread.php?t=1754078)[/INDENT]

No solutions yet... I believe the poster already filed a bug on this problem to launchpad.net, but I don't see a link for it there. I will add it to that thread...

---

### Post by Ouroborus777 on 2011-05-23
Ah, okay. Thanks for the link.

---

