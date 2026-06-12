---
title: "OpenGL Help!"
date: 2011-11-24
forum: General Help
---

### Post by Born2Phase on 2011-11-24
Hi, I'm relatively new to Ubuntu/Linux and so I don't really know what I'm doing and I'm hoping someone can help. 

I've run into an issue with OpenGL when trying to run a piece of software. Basically the program complains that the version of OpenGL I have is earlier than 2.0 and that it will disable some of it's features. I've checked the version I have using:

glxinfo | grep version > ~/Desktop/GLX.txt

and I get:

server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 1.5 Mesa 7.7.1

I checked my GPU using:

lspci |  grep VGA

and I get:

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3470

This should be able to support openGL 3.1

[http://www.amd.com/us/products/notebook/graphics/ati-mobility-hd-3000/hd-3400/pages/hd-3400-specs.aspx](http://www.amd.com/us/products/notebook/graphics/ati-mobility-hd-3000/hd-3400/pages/hd-3400-specs.aspx)

How do I go about updating the openGL version I have?

Any help at all would be appreciated

---

