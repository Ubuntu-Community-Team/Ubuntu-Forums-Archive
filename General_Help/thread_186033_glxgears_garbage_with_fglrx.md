---
title: "glxgears garbage with fglrx"
date: 2006-06-01
forum: General Help
---

### Post by jonibo on 2006-06-01
In Dapper, I'm getting the following garbage when I run glxgears... fglrx driver for Radeon Mobility 9000 installed.  Anyone else seen this, or any ideas...?

[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT

---

### Post by johnc4510 on 2006-06-01
I don't see the command your using, but it should be:
glxgears -printfps
I'm not sure about your API error

---

### Post by jonibo on 2006-06-01
Same garbage with glxgears -printfps
There's some other problem there...

---

### Post by nbx909 on 2006-06-01
what are some decent fps?

---

### Post by bollix47 on 2006-06-01
Paste your output from:

fglrxinfo

---

### Post by johnc4510 on 2006-06-01
It all depends on your graphics card. I have an old nvidia FX 5500 that gets about 61 fps, but I have seen some of the fast cards showing much higher. I don't play a lot of games so I don't need a really fast card.

---

### Post by barbarian on 2006-06-01
Hi, it's known ati bug:

[http://ati.cchtml.com/show_bug.cgi?id=373](http://ati.cchtml.com/show_bug.cgi?id=373)

---

### Post by jonibo on 2006-06-01
Same garbage with fglrxinfo... there's too many errors to post, but they are all the same... like the ones in the example output.

---

### Post by Ramses de Norre on 2006-06-01
[QUOTE=nbx909]what are some decent fps?[/QUOTE]
Depends on your graph card, I get something about 3420 fps with an ati x600.

---

### Post by Amt0571 on 2006-06-01
[http://www.ubuntuforums.org/showthread.php?t=185033](http://www.ubuntuforums.org/showthread.php?t=185033)

Go to this post and download the libGL.so.1.2, replace your current one with the one you downloaded, and provlem solved :)

---

