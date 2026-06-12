---
title: "Unity - odd behavior when switching windows"
date: 2011-05-24
forum: General Help
---

### Post by kenny3794 on 2011-05-24
I have an odd behavior where the Unity shell looks incorrect when switching windows with 3D cover-flow like behavior.  I created a video to demonstrate: 

[https://picasaweb.google.com/lh/photo/PiTP0NYnq1OaINpRaZO24j8X6TwLqN8Br2A7x-y3r6Y?feat=directlink](https://picasaweb.google.com/lh/photo/PiTP0NYnq1OaINpRaZO24j8X6TwLqN8Br2A7x-y3r6Y?feat=directlink)




When I run unity_support_test, all appears well:

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string:  3.3.10665 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes



Any help is appreciated.
Ken

---

### Post by sikander3786 on 2011-05-25
Welcome to the forums :)

Sorry I couldn't spot any incorrect behavior in that video, can you explain please?

---

### Post by kenny3794 on 2011-05-25
The incorrect behavior is the loss of the unity components (launcher, panel), they glitch and show some distorted form of the background.  Not debilitating in that sense, but quite annoying when quickly switching tasks.

I did find that when I initially installed, running Avant Window Navigator (left-over from before unity) would cause the launcher and panel to get stuck in this condition.  With that, I was unable to do anything but switch TTYs and reboot, as unity would not recover. 

Again, not a broken unity, but a nuisance in my case.  I always like to know if someone else is having the same problem and how they've fixed it.

Ken

---

### Post by wojox on 2011-05-25
I see what you mean. It happens to me as well when configuring compiz plugins. Seems like Unity does not always get along with the others.

---

