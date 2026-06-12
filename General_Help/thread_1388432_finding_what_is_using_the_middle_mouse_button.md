---
title: "finding what is using the middle mouse button"
date: 2010-01-23
forum: General Help
---

### Post by falkaholic on 2010-01-23
Is there some low-level way of listing which mouse button does what in Gnome?

It seems my middle mouse button is mapped to something besides a middle mouse click (button 3).

For example, to move or pan in apps like Xmind or blender, you need to click on hold the MMB. The app will work like expected for a split second then stop, making it useless.

This is one of the most frustrating issues I find with Gnome/Linux/etc. There is a million places to set global inputs, but no place to find them. I have been through every control panel, every compiz plugin, xorg, gconf etc, and can't find what the MMB is set too (or any other input for that matter). I know that somewhere MMB on a window title bar will send it to the back, but can't find where that is either. 

thanks for any help.

---

### Post by ankspo71 on 2010-01-23
> **falkaholic said:**
> I know that somewhere MMB on a window title bar will send it to the back, but can't find where that is either. 


Try looking in Apps > Metacity > General  inside gconf-editor.  Edit the entry called "action_middle_click_titlebar" and change it to 'lower'. That will send the window to the back if you middle click the title bar.

---

### Post by ankspo71 on 2010-01-23
Also, to move a window in any direction across your screen, hold the Alt key down and drag the window around with the left mouse button. In Ubuntu 9.04 this feature was buggy because nobody could drag a window completely upwards with compiz enabled, but this feature has improved in Ubuntu 9.10 (and 10.04 development release which is what I'm using now)
Hope this helps.
* note this feature doesn't work with maximised windows. *

---

### Post by falkaholic on 2010-01-23
> **ankspo71 said:**
> Try looking in Apps > Metacity > General  inside gconf-editor.  Edit the entry called "action_middle_click_titlebar" and change it to 'lower'. That will send the window to the back if you middle click the title bar.

Thanks, now I know where that one is.

---

### Post by falkaholic on 2010-01-23
Still no luck hunting this down, it isn't compiz for sure now.

Gone through all of gconf-editor.

What ever is overriding the MMB is also making Alt-MMB resize not work either. Hmmmmmm.

---

### Post by falkaholic on 2010-01-23
Ahh, seems it is the physical mouse. My Logitech RX300 seems to be the culprit. The middle mouse button has always felt a little different. Either some sort of driver bug, or this mouse thinks I am moving the scroll wheel every time I click MMB. Don't buy that mouse!

Used my old Logitech m-BJ69 and everything works as expected.

---

### Post by smilingfrog on 2010-04-11
The generic function of the middle button in Linux is to paste previously highlighted text. This, obviously, can be overridden in gnome.

---

### Post by coCoKNIght on 2010-05-18
I've got the same problem here. I'm trying to use Wings3D and most camera modes include dragging the middle mouse button to manipulate the view. Every second time I do this nothing will happen, instead lots of normal gnome buttons won't be clickable anymore until I press middle mouse button again... This is the case even when using Fluxbox. I haven't encountered this problem with older Ubuntu versions, so I don't think it has to do with the 'paste what was previously selected' thing. However just to be sure, how would I turn this functionality off?

---

### Post by lightstream on 2010-05-18
I don't know about Wings3D, but various Linux progs let you press and hold the middle mouse button in order to drag e.g. Eye of Gnome, if the image is larger than the visible area.

I don't know of a way to easily disable the middle-mouse paste feature.

Have you tried with another mouse? Middle mouse buttons often seem to be dodgy one way or another - like not sensitive enough, too sensitive etc etc

---

### Post by coCoKNIght on 2010-05-18
3D apps always use the middle mouse button, it's not for fun, it's because two buttons is not enough to use 3D apps...
However with Blender I don't have this problem I just realised, so maybe it has something to do with the current version of Wings3D, but not sure since there's definitely something strange happening with Gnome.

---

### Post by lsutiger on 2010-06-24
Slightly related....
When I had previous versions of Ubuntu (6.04 through 9.10), when I used a right/left click to emulate a middle click in a web browser, it opened the webpage in a new tab (firefox, opera, and chrome).
I installed 10.04 and now when I do a right/left click, a pop up menu appears asking me what I want to do. 

I changed the middlemouse.contentLoadURL in about:config in firefox to true, but that did not change the behaviour. And it is the same in chrome. I looked around in gconf-editor, but could not find the key to change.
Please help! I just installed 10.04 yesterday  and love the speed increase it has given me. I just want to perfect this installation like I had it in 9.04!

---

### Post by mehdadoo on 2010-07-08
Instead of "Alt + MMB" i do "Ctrl + ALt +MMB". Holding an extra Ctrl key did it for me!

---

### Post by falkaholic on 2010-07-12
I have had to go back to my RX300, my other mouse seems to have grown some other problems.

This problem still exists in 10.04 after a fresh install.

Strange, I don't think its a hardware issue. Holding Alt-MMB to resize window works, but other uses of MMB by itself seems to only last a split second. 

Wow, this is annoying. Is there a version of Onscreen Keyboard for mice? Is there a way to troubleshoot this on a low level?

thanks.

---

