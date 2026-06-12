---
title: "Compiz Cube, applications from last viewport on all sides"
date: 2010-04-19
forum: General Help
---

### Post by AnotherMuggle on 2010-04-19
I have managed to get Compiz Desktop Cube working with 4 viewports. Everything is great but I have noticed the that cube will show the running applications in the bottom panel, from the previously active viewport, on all sides of the cube.

Anyone know how to set it so that the bottom panel on each side of the cube displays only the applications that are running in the currently visible viewport?

I hope that's clear because I'm not 100% sure of the terminology.

Cheers,
Tom

EDIT: I just ran the Linux Mint 8 live CD which has Compiz Settings Manager included by default and it behaves in the same manner. For me this renders the cube useless because windows need to be open in a viewport in order to determine the viewport you are looking for.

---

### Post by P4man on 2010-04-20
When you say "bottom panel" do you mean the viewport switcher on the bottom gnome panel? It will always show desktop 1 ("cube side 1") on the left, 2 next to it, and so on. Im not quite sure what it is you'd want instead, you'd like it to show relative position? If so I dont think thats possible, you'd need a different panel applet for that.

That said, do you really need or want that? So many ways in compiz to organize and visualize your running apps. Experiment with Expo and window picker plugins, or just unfold cube (control alt down arrow, then left/right arrow),..

---

### Post by AnotherMuggle on 2010-04-20
> **P4man said:**
> When you say "bottom panel" do you mean the viewport switcher on the bottom gnome panel? It will always show desktop 1 ("cube side 1") on the left, 2 next to it, and so on. Im not quite sure what it is you'd want instead, you'd like it to show relative position? If so I dont think thats possible, you'd need a different panel applet for that.

That said, do you really need or want that? So many ways in compiz to organize and visualize your running apps. Experiment with Expo and window picker plugins, or just unfold cube (control alt down arrow, then left/right arrow),..

What I mean is, if my REAL desktop has, for example, Firefox, Pidgin and a Terminal open, and none of the other 3 desktops have anything running in them... when I open the cube and rotate around...all of the desktops have Firefox Pidgin and a Terminal visible on the bottom panel.  If I stop the cube on a desktop that actually has nothing open, then these applications in the bottom panel disappear.

---

### Post by P4man on 2010-04-20
Ah, when you say "Bottom panel" you are referring to the "window list" with buttons for each app which you can click to minimize/restore windows, like windows taskbar?

I suppose that is it since indeed it doesnt get refreshed while rotating the cube; some googling tells me its because compiz cube doesnt actually use different workspaces. I dont think there is a workaround or solution for that, although you can change the behavior of the window list at the bottom to show windows on all viewports (cube sides). If you think that helps, then just right click the window list applet (click just right of the show desktop button) and change the behavior in preferences menu to "show windows from all workspaces".

TBH though, I dont really see the problem as rotating the cube is just a gimmick, the novelty wears off quickly. Compiz has many more tools to work with multiple windows and viewports that are a lot more useful IMHO, like Expo and windows picker. I have windows picker across viewports linked to my middle mouse button, one click shows me all open windows nicely organised, click the window, and it rotates to the correct cube face. Very handy to find an app, much more so than rotating a cube and staring at the tiny window list at the bottom.

But YMMV.

---

