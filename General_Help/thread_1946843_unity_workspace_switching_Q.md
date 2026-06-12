---
title: "unity workspace switching Q"
date: 2012-03-25
forum: General Help
---

### Post by kurja on 2012-03-25
Is there a way to switch workspaces using only the mouse, or some key+mouse movement, or something like that? Like, in similar fashion to alt-dragging windows, press a key and drag to get to another workspace, or double click and hold the background to enable switching workspaces with mouse movement... or at least bring up the switcher when double clicking the background? Something?

---

### Post by kurja on 2012-03-27
Sorry about the bump but really, is there no way?

---

### Post by Krytarik on 2012-03-27
Firstly, you can obviously use the Launcher item meant for this very purpose, the Workspace Switcher :P - in both regular Unity and Unity 2D.

Secondly, if using regular Unity, and the Desktop Wall, you can bind workspace switching to ScreenEdge+Click, for example (I have it that way); therefore, set up the desired combinations under "CompizConfig Settings Manager -> Desktop Wall -> Bindings -> Move within wall", and if wished, also enable "Allow Wrap-Around" under the "Viewport Switching" tab (I have that enabled, too).

Regards.

---

### Post by stinkeye on 2012-03-27
Also have a look at easystroke mouse gestures.
You can use gestures to flip left or right, or bind a spare mouse button
to ccsm shortcut keys.

---

### Post by 3Miro on 2012-03-27
From CCSM you can set ViewPort Switcher to change workspaces on mouse-scroll over the desktop.

---

### Post by kurja on 2012-03-28
> **Krytarik said:**
> Firstly, you can obviously use the Launcher item meant for this very purpose, the Workspace Switcher :P - in both regular Unity and Unity 2D.

Obviously, but I'm looking for something a bit more "immediate" that would work without clicking a little there and a little here, and would work without pressing a bunch of buttons while breakdancing, you know ;)

> **Krytarik said:**
>  Secondly, if using regular Unity, and the Desktop Wall, you can bind workspace switching to ScreenEdge+Click, for example (I have it that way); therefore, set up the desired combinations under "CompizConfig Settings Manager -> Desktop Wall -> Bindings -> Move within wall", and if wished, also enable "Allow Wrap-Around" under the "Viewport Switching" tab (I have that enabled, too).

Regards.

Do you mean this? [http://askubuntu.com/questions/41058/how-can-i-enable-bindings-in-desktop-wall](http://askubuntu.com/questions/41058/how-can-i-enable-bindings-in-desktop-wall)

Might be quite much like what I was looking for, I'll give that a try.

---

### Post by kurja on 2012-03-28
> **3Miro said:**
> From CCSM you can set ViewPort Switcher to change workspaces on mouse-scroll over the desktop.

Thanks, I'll look into that too

---

### Post by Frogs Hair on 2012-03-28
There is move to workspace option when you right click the title bar also .

---

### Post by Krytarik on 2012-03-28
> **kurja said:**
> Do you mean this? [http://askubuntu.com/questions/41058/how-can-i-enable-bindings-in-desktop-wall](http://askubuntu.com/questions/41058/how-can-i-enable-bindings-in-desktop-wall)
Actually, I was only referring to the direct mouse bindings you can also see in the second screenshot there, but if it's indeed needed to work around any possible conflicts/bugs with Unity, or the current version of Compiz, reg. the screen edges, the "xdotool" method should work, too.

---

### Post by kurja on 2012-03-28
> **Frogs Hair said:**
> There is move to workspace option when you right click the title bar also .

Thanks, I didn't know that. Although it only serves to send a window to a workspace (I was looking for a way to get to a workspace) and it doesn't seem to work when a window is maximised - might that be called a feature or a bug, I don't know.

---

### Post by MadHatter93 on 2012-03-30
In Compiz Config Settings Manager, look for the Expo plugin, and set the option for Expo Button to whatever button configuration you want. You can choose edge+button, ctrl/alt/super+button, or just button options, depending on your preferences. Just make sure you don't nullify any other shortcuts.

---

### Post by Anencephalic on 2012-08-27
I just hold down <Ctrl>-<Alt>-<Left Click> and drag to another workspace. I'm not sure if I did anything to enable this or if it's stock, but I'm surprised that no one mentioned it. Am I missing something?

---

### Post by alecz20 on 2012-09-19
I am testing out Ubuntu 11.10 in a Virtual Machine to see if I should upgrade to it. One the most awesome things in Ubuntu and Linux in general is the workspace feature. I am able to much better organize my work.

However, I have been trying for about an hour to move a window to another workspace but I wasn't able.

Here, I am talking just basic Ubuntu, no other programs installed.

> **Krytarik said:**
> Firstly, you can obviously use the Launcher item meant for this very purpose, the Workspace Switcher :P - in both regular Unity and Unity 2D.


That's what I thought, but it does not work for me, or maybe I just don't have the "intuition".

What I do is click on the workspace swithcer, which kinda zooms out but shows me only the current workspace in the upper left quarter of the screen. I cannot click and move any windows not can I "go to" other workspaces like on older versions of Ubuntu.

I am trying to go with the flow and the new way of thinking of Ubuntu developers, so I would like to know what the the "intended" procedure to go to another workspace (using a mouse and the default programs).

This is what I get when I click on the workspace switcher:
[IMG]http://www.imagebam.com/image/2ed69b211341250[/IMG]
I read that Unity comes with 4 workspaces (as the icon shows as well), and that it is quite complicated to add more. So I just want to use those 4 anyway.

---

