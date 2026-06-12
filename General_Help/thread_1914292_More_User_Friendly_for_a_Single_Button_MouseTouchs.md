---
title: "More User Friendly for a Single Button Mouse/Touchscreen"
date: 2012-01-24
forum: General Help
---

### Post by mightybuddha on 2012-01-24
Hi Chaps,

I've built a touchscreen computer and it works wonderfully (apart from a little bug I posted about in another thread) though what would really make it **outstanding** would be a simple way to get right click/secondary click functionality.

I know there is an option in universal access for long touch triggers secondary click, though the touchscreen is too sensitive so it "jitters/shakes" around a few pixels when holding your finger down, and so it doesn't trigger the secondary click.

What would be good would be if I can hold down a function key (alt/crtl/fn/etc) and it would make the touchscreen register a right click instead of a left click.  So it would be like a keyboard shortcut where fn+button1 triggers the right click context menu.  But there is no option similar to this in keyboard shortcuts.

Is this possible?

Or if you know how to get long click working in this instance that would help to!

Cheers guys!

(ps. I know Shift+F10 triggers the menu though I don't think you can remap it, can you?)

---

### Post by evilsoup on 2012-01-24
I had a similar problem with my laptop, where I wanted to remap the 'menu' key to middle-click (so I don't have to press the left and right keys at the same time).

What I ended up using was xdotool; in the keyboard shortcut manager, I created (by clicking the 'Add' button and typing the command in the 'Command' box) a command using 

xdotool click 2

and bound it to the menu key. You would want to use

xdotool click 3

[CENTER][LEFT](which will create a left-click) and then bind it to a button. This is not a perfect solution, I'm not sure how to remap mouse keys to give you ctrl+click; if you mapped this to the 'menu' key, for example, you would have to move the pointer to the spot you want to right-click and then press the 'menu' key. Maybe this [thread]("http://ubuntuforums.org/showthread.php?t=1694352") might help with that part?

EDIT: I mean post #9 by Krytarik specifically
> I forgot to mention: You don't have to use the command line *at all* to achieve what you want. :wink:

1.) install "xdotool" through Synaptic

2.) go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"

- at the first tab, "Commands", enter the respective xdotool command:
 	Code:
 	xdotool key shift+a 
- at the tab "Button Bindings" assign the desired mouse button to the newly created command

Manpage of "xdotool":  [http://manpages.ubuntu.com/manpages/...xdotool.1.html]("http://manpages.ubuntu.com/manpages/maverick/en/man1/xdotool.1.html")

though you should use 

xdotool click 3

instead of 'xdotool key shift+a'; I can't really try this out now, so I don't know if this solution can give exactly what you want, but it looks like a good shot.
[/LEFT]
[/CENTER]

---

### Post by mightybuddha on 2012-01-24
thanks for the tip... xdotool may be able to do what I need but will have to have a read about its usage.

One thing I've been playing with is using the custom keyboard shortcuts with something like :


**"Right Touch"**
```
xinput set-button-map "ImPS/2 Generic Wheel Mouse" 3 2 1
```**ctrl+page up**


and 


**"Right Untouch"**
```
xinput set-button-map "ImPS/2 Generic Wheel Mouse" 1 2 3
```**ctrl+page down**


Which swaps the mouse buttons.  (I'm just testing this with another computer using a mouse since I don't have the machine in front of me).

Looks like this could be a work around if I could assign these commands to be executed on ctrl keydown and then execute the other command with ctrl keyup if you know what I mean.  

That way when I hold down ctrl, the left button acts as the right button and then goes back to normal on release.

xdotool looks like it may be able to do that so I'll have a play with it tonight and will let you know!

Cheers!

---

### Post by mightybuddha on 2012-01-26
SOLVED!

I wrote a tiny command based on the xinput settings in my previous post that changes the behavior of the touchscreen so that presses are interpretted as right clicks instead of left clicks for 3 seconds after pressing a hotkey.

For example, pressing ctrl+spacebar (or any combo or hotkey) could initiate the script and then for 3 seconds you can right click anywhere using the touchscreen, then after the 3 seconds the input changes back to it's normal left click behaviour.

Instructions here -> [http://needsmoresteam.com/ubuntu-touchscreen-problems-and-their-solutions/#rightclick](http://needsmoresteam.com/ubuntu-touchscreen-problems-and-their-solutions/#rightclick)

---

