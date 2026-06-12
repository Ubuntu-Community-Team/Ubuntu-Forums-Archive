---
title: "Non-working Shift + [Home|End|Arrow Keys] (ubuntu, nxclient, mac os x)"
date: 2011-06-05
forum: General Help
---

### Post by armalock on 2011-06-05
Hi all,

I have a very annoying issue that I am hoping someone can shed light to. I could not find any answer to this even though I have been looking for days.

When I connect to my ubuntu machine at work via NX (shadowing the existing session), I cannot select any text using the shift key. Shift key itself works (I can use it to capitalize letters for instance). It is just that arrow keys, page down/up keys, home/end does not work with shift. Without shift, they work (so I can navigate, just cant select).

I tried running xev to see the key events. In the local X11 session (XQuartz), keeping shift key pressed and pressing home prints the expected key press/release events. However, in the NX session, pressing shift prints "key pressed Shift_L" but then pressing home/end/page up/page down prints nothing. 

I have no problems with any of the other keys within the remote session. Alt, for instance, works perfectly fine (I can open menus, do alt_tab). Ctrl also works. Ctrl - arrow keys switches my desktops. Editing code is like nightmare because I have to constantly select text using the mouse. I can possibly remap the selection keys to some other combination but that's the last resort.

---

### Post by mavps on 2011-06-13
bump

---

### Post by armalock on 2011-06-14
It turned out to be a bug in NX.

I upgraded both the server and client from 3.4 to 3.5 and it worked. However I found 3.5 to be much less stable than its predecessor, so now I am just using xpra.

---

