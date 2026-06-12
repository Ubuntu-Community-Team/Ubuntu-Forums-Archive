---
title: "Where is object file after compiling?"
date: 2012-09-24
forum: General Help
---

### Post by elgnaw1006 on 2012-09-24
I wrote a simple helloworld program. After compiling .cpp file using  gcc, it output a file that i can excute in terminal. But there are only 2  files in my fold inlcluding helloworld.pp and helloworld. Where is the  object file?  And when I click on the excutable file,  helloworld, it  doesn't work. Why should it only be excuted in the terminal?

---

### Post by Foxcow on 2012-09-25
Usually, when people learn to program, they learn to make console programs.  Every "Hello World" program I've seen has been the most basic console prgram that is launched via command line.

On to compilation,

When using g++ to compile helloworld.cpp, most people invoke it by typing:
```

g++ helloworld.cpp

```

With no additional arguments, g++ will only produce an executable target.  Without delving too deep into what a compiler does, if you want to look at what a .o [object] file looks like, you can run:
```

g++ -c helloworld.cpp

```




Hopefully, that shed some light.

---

