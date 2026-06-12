---
title: "Compiz Alt+Scroll opacity and windows switching problem"
date: 2009-11-17
forum: General Help
---

### Post by Cesaar on 2009-11-17
I started using 9.10 recently and I was setting the visual settings of the interface on compiz. I tried enabling the opacity with the alt+scroll shortcut and it works well, besides the fact that this action also switches between windows. I'm not sure how to unset the switching. I've looked at all the relevant options in compiz but i can't find anything. Has anybody had this problem or knows how to fix it? All help is appreciated =] :KS

---

### Post by Bag-O-Stuff on 2009-11-17
If you click on "System -> Preferences -> Advanced Desktop Settings" and then go into the Advanced Search, type "<Alt>Button5" into the search box and search only the "Settings" values.  This will return all the bindings that use the Alternate Key and scroll down on the middle mouse button.  Searching for "<Alt>Button4" show which ones use the Alternate Key and scroll up on the mouse.

Find the one for the Window Switching and change the binding to something else and your Opacity should work normally again.

---

### Post by Cesaar on 2009-11-17
> **Bag-O-Stuff said:**
> If you click on "System -> Preferences -> Advanced Desktop Settings" and then go into the Advanced Search, type "<Alt>Button5" into the search box and search only the "Settings" values.  This will return all the bindings that use the Alternate Key and scroll down on the middle mouse button.  Searching for "<Alt>Button4" show which ones use the Alternate Key and scroll up on the mouse.

Find the one for the Window Switching and change the binding to something else and your Opacity should work normally again.

Thanks for your quick reply! I looked over in preferences but i don't have Advanced Desktop Settings in there. :(
Nonetheless, I tried searching what you said in the CompizConfig Settings Manager and only opacity showed up.

---

### Post by Cesaar on 2009-11-17
> **Cesaar said:**
> Thanks for your quick reply! I looked over in preferences but i don't have Advanced Desktop Settings in there. :(
Nonetheless, I tried searching what you said in the CompizConfig Settings Manager and only opacity showed up.

Actually, I looked up Advanced Desktop Settings and it seems to be the same as CompizConfig Settings Manager. But yeah, only opacity showed up. Maybe it's not a Compiz setting?

---

### Post by Dougie187 on 2009-11-17
Not sure if this will help or not. But did you change your window grab button in System->Preferences->Window to something other than Alt? I don't know if that will help or not, but it's worth a try.

Also, in the search, instead of searching for a specific button you could do "<Alt>Button" That way you should get all bindings for your mouse, and thus the scroll wheel.

---

### Post by Cesaar on 2009-11-17
Okay I solved the problem. It's actually the <Alt>Button6 configuration that Lowered my windows when I did alt+scroll down. It's weird, what's Button6? How would it activate by scrolling down? Anyways, thanks for your help!

---

### Post by arubislander on 2009-11-17
Maybe Button6 is your scroll button? Are you a heavy handed scroller (pressing the button as you scroll)?

---

### Post by Cesaar on 2009-11-17
> **arubislander said:**
> Maybe Button6 is your scroll button? Are you a heavy handed scroller (pressing the button as you scroll)?

I experimented a bit more and figured out what was happening. Button6 is left-scrolling. Since I'm using a mouse-pad and also two-finger-scrolling, the alt+Button6 which is alt+left-scrolling would activate since it is almost impossible to scroll perfectly downwards or upwards. That would activate the Lower Window setting. I found that ctrl+Button6 was set for Raise Window so I deactivated it. Button7 is right-scrolling.
 
In summary:
Button1 is left click(also one-finger-tap when enabled)
Button2 is middle click(also Button1 & Button3 when pressed at the same time OR three-finger-tap when enabled)
Button3 is right-click(also two-finger-tap when enabled)
Button4 is up-scroll
Button5 is down-scroll
Button6 is left-scroll
Button7 is right-scroll

Now, I wonder what Button8 and Button9 are...

---

