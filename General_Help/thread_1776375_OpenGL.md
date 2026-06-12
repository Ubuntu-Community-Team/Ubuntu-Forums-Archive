---
title: "OpenGL"
date: 2011-06-06
forum: General Help
---

### Post by lakshmen on 2011-06-06
where do i find these files ? 

#include <GL/glut.h>
#include <GL/gl.h>
#include <GL/glu.h>

do anyone know?

---

### Post by wildmanne39 on 2011-06-06
> **lakshmen said:**
> where do i find these files ? 

#include <GL/glut.h>
#include <GL/gl.h>
#include <GL/glu.h>

do anyone know?Hi, I am not sure where they are but I know that opengl is not to be changed in any way or you will probably get an unbootable system or no screen.

---

### Post by lakshmen on 2011-06-06
because, i dont have the files, i cant execute the functions....

i get this output when i link :
laksh1.cpp:(.text+0x239): undefined reference to `glClear'
laksh1.cpp:(.text+0x23e): undefined reference to `glLoadIdentity'
laksh1.cpp:(.text+0x24a): undefined reference to `glEnable'
laksh1.cpp:(.text+0x25f): undefined reference to `glBindTexture'
laksh1.cpp:(.text+0x2bb): undefined reference to `glTexImage2D'
laksh1.cpp:(.text+0x2c7): undefined reference to `glBegin'
laksh1.cpp:(.text+0x2ef): undefined reference to `glColor4f'
laksh1.cpp:(.text+0x305): undefined reference to `glTexCoord2f'


what should i do?

---

### Post by laserator on 2012-04-23
Hey, I have the same problem. Ive asked two or three times and I get no reply. 
<GL/glut.h> and the rest are in ~/lib/include I think. 
 
If you figure anything out let me know.
I have the files there but for some reason I still get undefined refrence errors. So IDk.

---

### Post by PeterP24 on 2012-04-23
@laserator
I think this thread may be closed because you replied to an old post (necromancy is called). The appropriate subforum to post your question would be in Programming Talk (not here). My guess for an answer would be that you neet to have libglut3-dev package installed.

---

