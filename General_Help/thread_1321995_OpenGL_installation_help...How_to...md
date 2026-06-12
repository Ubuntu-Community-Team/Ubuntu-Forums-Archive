---
title: "OpenGL installation help...How to..??"
date: 2009-11-10
forum: General Help
---

### Post by hakermania on 2009-11-10
hi guys! I was trying to enable the 3d chess mode in my ubuntu 9.10 and i took the following message:  "You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Please contact your system administrator to resolve these problems, until then you will be able to play chess in 2D mode."

As I understood I have to download and install OpenGL...Well, I searched a bit in other forums, and the answers given were a bit strange and difficult to understand...Can you please explain me how can I install openGL? Special thx guys! My graphic card is Mobile intel(R) 4 Series Express Chipset Family;)

---

### Post by honestguvnor on 2009-11-10
Go into system->admin->synaptic. Search on "python-opengl". Set it to be installed. Do likewise for python-gtkglexit. When it installs it will also install opengl if it is not already present because it is a dependency.

---

### Post by hakermania on 2009-11-10
> **honestguvnor said:**
> Go into system->admin->synaptic. Search on "python-opengl". Set it to be installed. Do likewise for python-gtkglexit. When it installs it will also install opengl if it is not already present because it is a dependency.

I installed python-opengl package successfully! But I searched for python-gtkglexit and there are no results...I can find python-gtkglext1....Do you mean that one?

---

### Post by Giblet5 on 2009-11-10
Try installing python-gtkglext1.

```
sudo apt-get install python-gtkglext1
```

Then restart the chess game and select 3D mode.

---

### Post by hakermania on 2009-11-10
> **Giblet5 said:**
> Try installing python-gtkglext1.

```
sudo apt-get install python-gtkglext1
```Then restart the chess game and select 3D mode.
Ok thx.that worked perfectly!!!):P):P

---

