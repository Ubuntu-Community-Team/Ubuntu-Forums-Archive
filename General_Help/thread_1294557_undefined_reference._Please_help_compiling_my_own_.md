---
title: "undefined reference. Please help compiling my own code with X11."
date: 2009-10-18
forum: General Help
---

### Post by born2net on 2009-10-18
Hello and thanks for reading this.
I developed a simple GUI c++ application .
I am trying to compile it and I included the Xlib.h header file since I need some of the functions in it.

I am using Scons to compile the code.
My compile line looks like this:

Program('SignageController', ['../stdafx.cpp', '../ByteArray.cpp', '../WindowFinder.cpp', '../LimitSingleInstance.cpp', '../ServerSocket.cpp', '../ProcessManager.cpp', '../Dispatcher.cpp', '../SignageController.cpp'], CCFLAGS='-g -DLINUX',  LIBPATH = ['/usr/X11R6/bin'])


When I compile I get an undefined reference to `XMoveResizeWindow'.

It seems that I am missing the library for my header file.

Can you please tell me where and HOW to download the correct X11 source libs so I can link to them and get rid of the undefined reference  error ?


Thanks again for reading this,

Alon - [http://MediaSignage.com](http://MediaSignage.com)

---

