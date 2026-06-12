---
title: "OpenGL SuperBible 5thedition+ codeblocks=how to compile?"
date: 2011-09-01
forum: General Help
---

### Post by loolooyyyy on 2011-09-01
all the projects in the book include these files:

#include <GLTools.h>
#include <GLShaderManager.h>

i've downloaded these files like this from googlecodes:

```

#user@pc:~$  ls
include/ src/

#user@pc:~/include$ ls
GL/
GLFrame.h              GLMatrixStack.h    GLTriangleBatch.h
GLBatchBase.h  GLFrustum.h            GLShaderManager.h  math3d.h
GLBatch.h      GLGeometryTransform.h  GLTools.h          StopWatch.h

#user@pc:~/include/GL$ ls
glew.h  glxew.h  wglew.h

=======================

#user@pc:~/src$ ls
GLBatch.cpp  GLShaderManager.cpp  GLTriangleBatch.cpp
glew.c       GLTools.cpp          math3d.cpp

```

now i want to compile a project in codeblocks, what should i do? i'm totally confused here, which of XXX.h and XXX.cpp files do i need and where should i put them? 
by the way i dont want to put them in /usr/include/  if possible, but here: /home/user/project/  and using "GLTools.h" instead of <GLTools.h>
project happens to be codeblocks project directory 

now, should i compile GLTools.cpp while compiling main.cpp? how? (in codeblocks)

---

