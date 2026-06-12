---
title: "Developing Games for Ubuntu"
date: 2009-09-23
forum: General Help
---

### Post by elasolova on 2009-09-23
Hi,
I want to develop open source games for ubuntu. I have decent knowledge in C++ and Python. Can you refer me to some direction as I am new to game development?

---

### Post by Simian Man on 2009-09-23
SDL is probably the best place to start.  It is written in C, so you can use it directly from C++, but there is also a popular Python binding called PyGame.  The best place to start learning SDL for C++ is [Lazy Foo's SDL tutorials.]("http://www.lazyfoo.net/SDL_tutorials/index.php")

---

### Post by elasolova on 2009-09-23
Thanks,

Yeah I heard about both of them. So they are both 2d based right? 
As a beginner I should probably start with 2d, but I think there is a 3d game engine called panda 3d for python (which uses opengl I suppose). Is it easy to use panda 3d?

---

### Post by Simian Man on 2009-09-23
> **elasolova said:**
> Thanks,

Yeah I heard about both of them. So they are both 2d based right?
Yep, but SDL can be used in conjunction with OpenGL for 3D games.  In this scenario, SDL does all of the stuff (window management, input, fonts, images, sound, networking...) except for 3D graphics which OpenGL handles.


> **elasolova said:**
> As a beginner I should probably start with 2d, but I think there is a 3d game engine called panda 3d for python (which uses opengl I suppose). Is it easy to use panda 3d?

I have never used panda, but looking over their website it actually sounds pretty cool!  Using an engine is definitely recommended for writing 3D games because otherwise building the infrastructure will take you forever.

---

