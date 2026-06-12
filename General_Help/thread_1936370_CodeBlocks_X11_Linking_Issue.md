---
title: "CodeBlocks X11 Linking Issue"
date: 2012-03-05
forum: General Help
---

### Post by addisonElliott on 2012-03-05
I am not 100% sure if this is the best place for this thread, but I did try finding a category that would suit it best, and I did not find anything related, so I thought General Help was the best :P

I am working on a client using OpenGL and I want it to be cross-platform so I am using GLX & X11, and WGL and WinAPI to make sure it works on most platforms. I am having a small issue with GLX & X11, and I can't seem to figure out why. 

The error I am getting is: "Undefined reference to 'OpenGL::Init(_XDisplay*, unsigned long)'.
The reason is says _XDisplay* is because Display is just _XDisplay.


Here is my code(I am just giving you the crucial information and what I include in each one in case I'm including something not needed):
Main:
#include <GL/GLX.h>
#include <X11/Xlib.h>

Init(display, window);

OpenGL.hpp
#include <GL/GLX.h>
#include <X11/Xlib.h>

bool Init(Display *dis, Window win);

OpenGL.cpp
#include "openGL.hpp"

bool Init(Display *dis, Window win)
{
    return true;
}

The weirdest thing about this error, is that if I remove the dis parameter completely, the error disappears. So this is why I brought it to a Ubuntu forum, because you probably know a lot more about X11 & GLX than me :P

---

