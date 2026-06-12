---
title: "compiz huge performance loss"
date: 2011-06-29
forum: General Help
---

### Post by gufide on 2011-06-29
I see a huge performance loss in compiz in 11.04 with two event:

1.Switching workspace
2.Resize window

For the workspace, by switching very fast form workspace to another, frame per second depend by the number of window:
0 Window: 60 frame/sec
1 Window: 30 frame/sec
2 Window: 22 frame/sec
3 Window: 15 frame/sec
4 Window: 10 frame/sec
5 Window: 7 frame/sec

And I think you understand...
I see that it's not the switching animation the problem, but before the animation. When I got a lot of window open, I can see that the animation got 60 frame/sec, but waiting/lagging a bit before and using 100% of CPU during the lag. Strangely, the animation time like to include the lag in the step (if the lag is bigger, the animation is faster)

For the resize action, when using the normal mode to resize, got about to two frame/sec with nautilus, in kde, it's fine, an metacity almost perfect. This is so hard to make a window resizing with 60 frame/sec?

I hope someone will react to this thread an fix the error, I'm not good enough in c++ :(
If you got this problem too, then I will be able to report the problem in launchpad.

---

### Post by RoyLongbottom on 2011-06-29
[FONT=Verdana][SIZE=2]Look into Wait For Vertical Refresh (Vsync)[/SIZE][/FONT]
[SIZE=2] [/SIZE]

---

### Post by gufide on 2011-06-30
I checked it. It's enabled. In compiz and in NVidia settings

---

### Post by RoyLongbottom on 2011-06-30
[FONT=Verdana][SIZE=2]I know nothing about compiz and don’t understand your problem but the FPS figures suggest that speed is limited by VSYNC being set, that is no higher than 60 FPS with one thing running, half that with two things and so on. [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]I have had cases where both the program and the graphics driver impose VSYNC, resulting in a maximum speed of 30 FPS.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

