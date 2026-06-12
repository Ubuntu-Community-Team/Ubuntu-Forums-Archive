---
title: "Cannot seem to get &quot;include&quot; file headers included"
date: 2011-03-09
forum: General Help
---

### Post by Daanii on 2011-03-09
I'm trying to do some development work in Ubuntu that I used to do in VisualStudio. I'm using SDL and OpenGL. To print text, I need to include the header file SDL_ttf.h 

Though I had trouble installing the SDL_ttf libraries, I think they are there now. But when I try to run the program using the following command line
```
g++ VideoTest.c -o VideoTest -lGLU -lSDL -lGL
```I get the error that 
```
VideoTest.c:4: fatal error: SDL_ttf.h: No such file or directory
```My suspicion is that I have not put the files in the right places. But I'm not sure which files need to go where, or how to get them there. 

Thank you.

---

