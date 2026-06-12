---
title: "Dumbest power button &quot;feature&quot; ever - help"
date: 2011-10-14
forum: General Help
---

### Post by bds1904 on 2011-10-14
Ubuntu 11.10

One complaint, when I press the power button it asks me a question.  Every other OS in the world lets me select what I want done when my power button is pressed in the "power configuration".  In 11.10 this feature is gone and I have to deal with a dumb question every time I hit the power button.

I want the power button to hibernate the PC.

When I hit the power button on my laptop I do it because I don't want to mess with the touchpad, and 11.10 is making me do it every single time now because of a dumb "feature".

Little, but annoying.

Any ideas how to fix it?

---

### Post by crdlb on 2011-10-15
There seems to be a bug here. Open dconf-editor and navigate to org.gnome.settings-daemon.plugins.power. button-power is set to suspend by default, but it acts like it is set to interactive. If you explicitly set it here, it should take effect.

P.S. I agree that this setting shouldn't be buried, whatever the default.

---

### Post by vitaly82 on 2011-10-15
I set button-power to hibernate there, but now it goes to sleep mode when I press power button...

---

### Post by joosth87 on 2011-10-18
I've 'resetted' the power button action in gconf to suspend and now it suspends like it should.

---

### Post by LaptopU on 2011-10-18
Thanks for the tip about dconf-tools.  I have set my power button to shutdown but my system doesn't always shut down - out of five sessions it probably shuts down four but fails one and I have to press the power button again, then it shuts down.

Any ideas?

Thanks.

---

### Post by LaptopU on 2011-10-20
Has anyone any idea please?  It is now pretty much every time I press the power button and my system doesn't shut down, the top bar goes from the default scheme to a light grey then goes back to default after about 10 seconds, then if I press the power button again it then shuts off (no messages in any of this).

(This is with dconf-editor power setting to 'shutdown' upon power button press).

---

