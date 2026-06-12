---
title: "eeepc CAPS lOcK Issue"
date: 2009-07-24
forum: General Help
---

### Post by t4thfavor on 2009-07-24
I have a 900a, and run 9.04 no netbook remix. My problem lies in the fact that there is no visual indicator that the CAPS LOCK key is on or off. This is made even worse by the fact that it sits right next to the 'a' key, and the keys are already tiny. So when I go to type an 'a', I regularly get both an 'a' and the CAPS LOCK key. then when I go to type other things, like passwords, etc I never know if iim going to get it rignt due too caps..


Does anyone know how to give a visual indicator that the caps lock key is on or off? Maybe in the notification area, or one of those nifty popups that show signal for wireless, volume, or brightness.

It would be great if someone knows a fix.

Thanks

---

### Post by mike555 on 2009-07-25
You could install "xkeycaps" and remap the capslock to something else .......

---

### Post by CatKiller on 2009-07-25
You could always go to System &#8594; Preferences &#8594; Keyboard &#8594; Accessibility &#8594; Audio Feedback and tick the "Beep when a toggle key is pressed" box.

---

### Post by t4thfavor on 2009-07-25
> **mike555 said:**
> You could install "xkeycaps" and remap the capslock to something else .......

Any ideas? What does everybody else use it for, I can see it being useful with a typewriter(?) but on a laptop, its not useful at all.

---

### Post by CatKiller on 2009-07-25
> **t4thfavor said:**
> What does everybody else use it for

The options that are widespread enough to be included in the Keyboard Layout Options are

Make CapsLock an additional Ctrl
Make CapsLock an additional Backspace
Make CapsLock an additional ESC

You could also make CapsLock a Compose key, or use it to change to the third level. Or just map it to A, since that's when you're most likely to hit it by accident.

All of these except the last one are just options in the Keyboard Layout Options window.

---

### Post by ibuclaw on 2009-07-25
Ensure that Caps Lock is turned off, then put this in your ~/.profile file
```
xmodmap -e "remove lock = Caps_Lock"
```
And run it in a terminal to ensure that it gets set for your current session, then Voila, CAPSLOCK is disabled.

Regards
Iain

---

### Post by ibuclaw on 2009-07-25
Alternately, an overblown way to do it, if you have Compiz enabled + Ubuntu's Notify daemon installed, you can add a hook so that you get a notification when you press the caps lock key, and the status that it is set to.

Check out the attached tarball for instructions, etc.

And see the attached screenshots for them in action (Grey == Caps Off, Blue == Caps On, although this can be changed if proves confusing).


I did try making it so that the notifications would change the title in synchronous, but it didn't appear to change in the testing I did. Perhaps this is a bug...


Regards
Iain

---

### Post by t4thfavor on 2009-07-27
All good ideas, but  like the last one. I will still probably just disable it though.

---

