---
title: "Do I have support for OpenglSL?"
date: 2011-12-21
forum: General Help
---

### Post by ibrabeicker on 2011-12-21
I'm reading "The OpenGL Shading Language Cookbook" and one of the first code examples that gets the vendor, version etc of opengl returns 

GL Vendor: (null)
GL Renderer : (null)
GL Version (string) : (null)
GL Version (integer) : -1079710564.12989220
GLSL Version : (null)

the code to get those values is

```
const GLubyte *renderer = glGetString( GL_RENDERER );
    const GLubyte *vendor = glGetString( GL_VENDOR );
    const GLubyte *version = glGetString( GL_VERSION );
    const GLubyte *glslVersion = glGetString( GL_SHADING_LANGUAGE_VERSION );
```Do I have support for OpenGL SL at all? even tho those values are null I've already made some opengl (no shading) programs before on my notebook. I thought mesa already had the implementation for SL and opengl 3.0+. Any idea of what's going wrong?

Ubuntu 11.11 32 bits
Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (core i3)
with glu, glut glew installed

EDIT: also 

GLuint vertShader = glCreateShader(GL_VERTEX_SHADER);

gives an error

undefined reference to `__glewCreateShader'

---

### Post by ibrabeicker on 2011-12-22
> **ibrabeicker said:**
> I'm reading "The OpenGL Shading Language Cookbook" and one of the first code examples that gets the vendor, version etc of opengl returns 

GL Vendor: (null)
GL Renderer : (null)
GL Version (string) : (null)
GL Version (integer) : -1079710564.12989220
GLSL Version : (null)

the code to get those values is

```
const GLubyte *renderer = glGetString( GL_RENDERER );
    const GLubyte *vendor = glGetString( GL_VENDOR );
    const GLubyte *version = glGetString( GL_VERSION );
    const GLubyte *glslVersion = glGetString( GL_SHADING_LANGUAGE_VERSION );
```Do I have support for OpenGL SL at all? even tho those values are null I've already made some opengl (no shading) programs before on my notebook. I thought mesa already had the implementation for SL and opengl 3.0+. Any idea of what's going wrong?

Ubuntu 11.11 32 bits
Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (core i3)
with glu, glut glew installed

EDIT: also 

GLuint vertShader = glCreateShader(GL_VERTEX_SHADER);

gives an error

undefined reference to `__glewCreateShader'

Answering my own problem, turns out mesa3d is lagging behind in the implementation of OpenGL and they are currently on version 2.1 of OpenGL, that does not support the standard of the book or the most recent shaders.

I'll either have to use a computer with ati/nvidia cards or develop on windows, that looks like have intel drivers that support the latest OpenGL

---

