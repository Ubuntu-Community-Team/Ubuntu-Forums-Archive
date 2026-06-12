---
title: "help with opengl"
date: 2009-08-17
forum: General Help
---

### Post by rednauj on 2009-08-17
I make a hello world of opengl in c++ and when I try to run it this occcur

g++ 2.cpp -o 2.o `sdl-config –cflags –libs` -lGL -lGLU
Usage: sdl-config [--prefix[=DIR]] [--exec-prefix[=DIR]] [--version] [--cflags] [--libs] [--static-libs]
2.cpp:1:21: error: GL/glut.h: No such file or directory
2.cpp: In function ‘void main_loop_function()’:
2.cpp:11: error: ‘GL_COLOR_BUFFER_BIT’ was not declared in this scope
2.cpp:11: error: ‘GL_DEPTH_BUFFER_BIT’ was not declared in this scope
2.cpp:11: error: ‘glClear’ was not declared in this scope
2.cpp:13: error: ‘glLoadIdentity’ was not declared in this scope
2.cpp:15: error: ‘glTranslatef’ was not declared in this scope
2.cpp:17: error: ‘glRotatef’ was not declared in this scope
2.cpp:19: error: ‘GL_QUADS’ was not declared in this scope
2.cpp:19: error: ‘glBegin’ was not declared in this scope
2.cpp:20: error: ‘glColor3ub’ was not declared in this scope
2.cpp:20: error: ‘glVertex2f’ was not declared in this scope
2.cpp:24: error: ‘glEnd’ was not declared in this scope
2.cpp:26: error: ‘glutSwapBuffers’ was not declared in this scope
2.cpp: In function ‘void GL_Setup(int, int)’:
2.cpp:33: error: ‘glViewport’ was not declared in this scope
2.cpp:34: error: ‘GL_PROJECTION’ was not declared in this scope
2.cpp:34: error: ‘glMatrixMode’ was not declared in this scope
2.cpp:35: error: ‘GL_DEPTH_TEST’ was not declared in this scope
2.cpp:35: error: ‘glEnable’ was not declared in this scope
2.cpp:36: error: ‘gluPerspective’ was not declared in this scope
2.cpp:37: error: ‘GL_MODELVIEW’ was not declared in this scope
2.cpp: In function ‘int main(int, char**)’:
2.cpp:41: error: ‘glutInit’ was not declared in this scope
2.cpp:42: error: ‘glutInitWindowSize’ was not declared in this scope
2.cpp:43: error: ‘GLUT_RGB’ was not declared in this scope
2.cpp:43: error: ‘GLUT_DOUBLE’ was not declared in this scope
2.cpp:43: error: ‘glutInitDisplayMode’ was not declared in this scope
2.cpp:44: error: ‘glutCreateWindow’ was not declared in this scope
2.cpp:45: error: ‘glutIdleFunc’ was not declared in this scope
2.cpp:47: error: ‘glutMainLoop’ was not declared in this scope

---

### Post by jespdj on 2009-08-17
Do you know how to program? The error message is quite clear:

**error: GL/glut.h: No such file or directory**

Install a package that provides the header file you need. On [http://packages.ubuntu.com](http://packages.ubuntu.com) you can search for packages that contain the file glut.h. You should install the package freeglut3-dev:

```
sudo apt-get install freeglut3-dev
```

---

