---
title: "[Ubuntu 10.04] Disable 3rd-mouse-button emulation forever"
date: 2011-08-13
forum: General Help
---

### Post by HighPerformer on 2011-08-13
I'm facing this problem since a while. I think its because the relevant xorg.conf entry no longer has effect because the matching piece of code was moved out of xorg.

I want to disable 3rd-mouse-button emulation forever, because it causes a delay of 50 milliseconds for the left mouse button and the right mouse button.

Usually you can disable the emulation by clicking the middle-mouse-button, but this is not persistent. I would like to delete it forever and not think of it every time.

I use a KVM-switch and 3rd-mouse-button emulation is re-enabled every time I switch the computer, because the system seems to think "Ah, a new mouse button has been plugged in, but I am not sure whether it has a third mouse button, so I better emulate it until the user proofs it has a third mouse button by clicking the third mouse button".

I don't want the system to behave like that. I want the third mouse button emulation to be disabled persistently over reboots, replugging, forever and for every device. How can I achieve that?

The solution must not necessarily be clean (I edit binaries if necessary). It should be free of side effects though.

---

