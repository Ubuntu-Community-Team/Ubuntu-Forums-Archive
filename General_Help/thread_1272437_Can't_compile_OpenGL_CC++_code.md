---
title: "Can't compile OpenGL C/C++ code"
date: 2009-09-22
forum: General Help
---

### Post by gane_starbuck on 2009-09-22
Hi,
I need help to figure out how to compile my OpenGL code using C/C++. I have looked around at other threads and tried their solutions without success. I would appreciate if someone could look at this short example (just to get GLUT running) and help me. 

```
#include <GL/glut.h>
#include <stdlib.h>

void renderScene(void) {
  glClear(GL_COLOR_BUFFER_BIT);
  glBegin(GL_TRIANGLES);
  glVertex3f(-0.5, -0.5, 0.0);
  glVertex3f(0.5, 0.0, 0.0);
  glVertex3f(0.0, 0.5, 0.0);
  glEnd();
  glFlush();
}

int main(int argc, char** argv) {
  glutInit(&argc, argv);

  glutInitWindowPosition(100,100);

  glutInitWindowSize(320,320);

  glutInitDisplayMode(GLUT_DEPTH | GLUT_SINGLE | GLUT_RGBA);

  glutCreateWindow("GLUT");

  glutDisplayFunc(renderScene);
 
  glutMainLoop();
  
}

```And here is trying to compile:

```
gane@upp-till-kamp-1-linux:~/Documents/3D-graphics/$ g++ GLUT.cpp -Iglut -IGL
/tmp/ccAqQ72y.o: In function `main':
GLUT.cpp:(.text+0x18): undefined reference to `glutInit'
GLUT.cpp:(.text+0x27): undefined reference to `glutInitWindowPosition'
GLUT.cpp:(.text+0x36): undefined reference to `glutInitWindowSize'
GLUT.cpp:(.text+0x40): undefined reference to `glutInitDisplayMode'
GLUT.cpp:(.text+0x4a): undefined reference to `glutCreateWindow'
GLUT.cpp:(.text+0x54): undefined reference to `glutDisplayFunc'
GLUT.cpp:(.text+0x59): undefined reference to `glutMainLoop'
/tmp/ccAqQ72y.o: In function `renderScene()':
GLUT.cpp:(.text+0x6e): undefined reference to `glClear'
GLUT.cpp:(.text+0x78): undefined reference to `glBegin'
GLUT.cpp:(.text+0x90): undefined reference to `glVertex3f'
GLUT.cpp:(.text+0xa3): undefined reference to `glVertex3f'
GLUT.cpp:(.text+0xb6): undefined reference to `glVertex3f'
GLUT.cpp:(.text+0xbb): undefined reference to `glEnd'
GLUT.cpp:(.text+0xc0): undefined reference to `glFlush'
collect2: ld returned 1 exit status
```As I understand it I have all GLUT and OpenGL libraries that is needed. (When i remove them I get the same error plus, of course, missing <GL/glut.h>)

Please help, I don't want to leave for DirectX because of an annoying minor error such as this.

/Starbuck

---

### Post by SeanHodges on 2009-09-22
You have specified the OpenGL headers you want to use, but you haven't added the associated libraries yet. This should do it:

g++ test.cpp -Iglut -lglut

The extra -l switch tells g++ to link your executable with the libglut library.

---

### Post by gane_starbuck on 2009-09-22
> **Re: Can't compile OpenGL C/C++ code** 			
 			 			 		   		 		 		You have specified the OpenGL headers you want to use, but you haven't added the associated libraries yet. This should do it:

g++ test.cpp -Iglut -lglut

The extra -l switch tells g++ to link your executable with the libglut library.


I don't really understand what you mean there. You used "-Iglut" twice? Anyway, if you look at my compile line you can see that I did use -Iglut and it didn't work. (I also tried it your way and no success). Do you have any other idea?

---

### Post by scragar on 2009-09-22
It's -I to set an include path, -l to specify a library.
```
g++ test.cpp -I/usr/include/GL -lglut
```
I think that's right. Easiest way would of course be to do```
locate glut.h
```

---

### Post by gane_starbuck on 2009-09-22
Thank you! It solved the problem.

---

### Post by gane_starbuck on 2009-09-22
Also, now that I see it. The first response solved it as well. I did not see the difference between [FONT=Times New Roman]I and l. Thanks both of you.[/FONT]

---

