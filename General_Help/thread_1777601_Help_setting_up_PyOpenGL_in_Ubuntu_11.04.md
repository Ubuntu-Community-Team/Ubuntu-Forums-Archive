---
title: "Help setting up PyOpenGL in Ubuntu 11.04"
date: 2011-06-07
forum: General Help
---

### Post by neurobot on 2011-06-07
I'm trying to set up openGL to use in python 3.2.  I have set up PyQt4.  When I'm running python3.2, I can type in the command ```
from PyQt4 import QtOpenGL
```, and it returns no errors.  But I can't import OpenGL. I'm new to python, I still can't figure out where the modules are located.  And I have no idea how to add modules.  I've downloaded PyOpenGL-3.0.1, but I don't know what to do with it.  

 I have been searching through forums and tutorials all day trying to get this to work, but I can't find a comprehensive tutorial explaining how to set up PyOpenGL in Ubuntu anywhere.  Any help is appreciated.

---

### Post by ultramanjones on 2011-07-10
> **neurobot said:**
> I'm trying to set up openGL to use in python 3.2.  I have set up PyQt4.  When I'm running python3.2, I can type in the command ```
from PyQt4 import QtOpenGL
```, and it returns no errors.  But I can't import OpenGL. I'm new to python, I still can't figure out where the modules are located.  And I have no idea how to add modules.  I've downloaded PyOpenGL-3.0.1, but I don't know what to do with it.  

 I have been searching through forums and tutorials all day trying to get this to work, but I can't find a comprehensive tutorial explaining how to set up PyOpenGL in Ubuntu anywhere.  Any help is appreciated.

I am not familiar with PyQt4, but as far as installing PyOpenGL-3.0.1 (which I'm guessing you'll want for the shader convenience module), start here and see if this helps:
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

I hope that helps!

---

### Post by ultramanjones on 2011-07-11
I'm not sure if my last post was helpful at all.  So I went and figured out how to install PyOpenGL-3.0.1 on my Ubuntu 10.04 LTS machine (I was planning on doing this anyway) and it's really much simpler than I thought, once I figured it out.

Check out this link.  Again, I hope it is helpful!

[http://ultraopengl.blogspot.com/2011/07/installing-pyopengl-301.html]("http://ultraopengl.blogspot.com/2011/07/installing-pyopengl-301.html")

---

