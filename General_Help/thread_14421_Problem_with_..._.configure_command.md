---
title: "Problem with ... ./configure command :|"
date: 2005-02-07
forum: General Help
---

### Post by Kimimaro on 2005-02-07
Ok.. I guess I'm starting to seriously annoy people on this forum... sorry  :sad: 

But now, after I have installed "gcc" program (in odrer to be able to run ./configure command for ANY program I want to install afterwards) ... and I try to run ./compile I get the following error :

"
(...) <- many gizmo fancy words I dont even understand  :mrgreen: (...)
checking for main in -ldl... yes
checking for main in -lm... yes
checking for location of tclConfig.sh... configure: error: tclConfig.sh not found - use the --with-tcl option
" :confused:

---

### Post by az on 2005-02-07
You shoudl install build-essential, not just gcc.

It looks like you need some developmental packages.  look for the -dev packages for the libs you are needing.  (tclx8.4-dev)

---

### Post by Kimimaro on 2005-02-07
That actualy worked! :)
But now again I face a problem that I need help with...
As usual ... the log :
"
checking for SDL - version >= 1.2.0... yes
checking for SDL_JoystickOpen... no
*** This version of SDL doesn't have joystick support.
*** Configuring without joystick support.
checking for Mix_OpenAudio in -lSDL_mixer... no
*** SDL_mixer not found.  Configuring without audio support.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
*** Hmm, you don't seem to have OpenGL libraries installed in the standard
*** location (/usr/lib).  I'll check in /usr/X11R6/lib, since
*** many distributions (incorrectly) put OpenGL libs there.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
configure: error: Cannot find GL library
"
... help ?

---

### Post by Xian on 2005-02-07
Have you set up X to load the GLX / DRI modules? 
Do you have the glx packages installed?

---

### Post by Kimimaro on 2005-02-07
...a what ?  :D

---

