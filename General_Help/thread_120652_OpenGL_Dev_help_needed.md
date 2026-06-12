---
title: "OpenGL Dev help needed"
date: 2006-01-23
forum: General Help
---

### Post by Jeigh on 2006-01-23
Hello, I've just started wanting to toy around with opengl a bit. I think it would allow me an easy way to accomplish something for my current job. However, after installing what I thought was all the packages I would need I tried compiling some example's off websites and they all say that references to the various openGL commands are not defined. I've tried to find a tutorial that would show my errors but to no avail.

What I was hoping someone could do for me is give an ubuntu specific, step by step (from begininning to end since I probably missed something on the way) procedure of which packages to install, any other files I would need, and if I need to add anything special to the command line compile command.

I was interested in using GLUT but just because it seemed like it was good for beginners, but if you can show me how to get something else up and running thats better then nothing. Thanks for any help in advance. (I'm running Ubuntu 5.10 if that is relevant)

---

### Post by fct on 2006-01-23
**GLUT**
Install GLUT for development:

$ sudo apt-get install libglut3-dev

To compile a source file for glut:

$ gcc -lglut file.c

Other library to use OpenGL is SDL:

**SDL**

$ sudo apt-get install libsdl1.2-dev

Compile source for SDL:

$ gcc `sdl-config --libs --cflags` file.c

Plenty of resources (tutorials, articles, example source) at [www.libsdl.org](www.libsdl.org)

**OpenGL info**

Wonderful tutorials with code for several libraries at:

[http://nehe.gamedev.net](http://nehe.gamedev.net)

---

### Post by jazzgossen on 2006-01-23
I would recommend SDL. It's more powerful, and I don't think it's more complicated to get it running.

---

### Post by Jeigh on 2006-01-23
Ah, as I expected it was jsut the -lglut that I was missing. I figured it was just having to tack something onto it but the sites I checked all seemed to ignore the fact. Maybe I just had bad luck with which I chose. Ah well. Thanks man!

---

