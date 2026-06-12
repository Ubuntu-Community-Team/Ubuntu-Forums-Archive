---
title: "libglu.so.1 not found?"
date: 2010-08-03
forum: General Help
---

### Post by X5-655 on 2010-08-03
I'm trying to run Kega Fusion on my laptop, which can now FINALLY run Linux (ATI drivers finally work on it), and I can't get the emulator to work..

```
brandon@brandon-laptop:~/Desktop/Fusion$ ./Fusion
./Fusion: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory
brandon@brandon-laptop:~/Desktop/Fusion$ uname -a
Linux brandon-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
brandon@brandon-laptop:~/Desktop/Fusion$ 
```

Help?  I have the ATI proprietary drivers installed.  I tried without them and it still wouldn't work.  (And OpenGL is seemingly working as Compiz Fusion is running.  I also tried with Compiz disabled but the same error pops up).

---

### Post by X5-655 on 2010-08-03
Ok I just installed GLTron, and it runs, so I know OpenGL is working.

---

### Post by Zorgoth on 2010-08-04
Try creating such a file linking to a similarly named file.

(in the directory /usr/lib)

You can make a symbolic link using the command "ln -s"

---

### Post by X5-655 on 2010-08-04
I forgot to update this thread, oops.

I installed ia32-libs and the app now loads and works great.

---

