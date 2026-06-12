---
title: "Eclipse IDE for C/C++ - &quot;undefined references&quot; error when the references are there."
date: 2012-04-16
forum: General Help
---

### Post by ldt on 2012-04-16
I love the Eclipse IDE for C++. It does everything I need to do easily and conveniently. However, getting a new project up and running can be a nightmare. I've had a number of problems with getting the preferences set to work. For most of them up to now I have been able to "trial and error" my way into a work around. However, I'm stumped on this one. I can't get the Debug build to work no matter what I try.

I have two projects. Both depend on the same two libraries "Lib1" and "Lib2". The first "Demo" is working. My new one "SIP" will not work for the Debug build. The Release build works as expected and I can see no differences in the preferences other than the optimizations and debugging options.

Here is the linker step of the "Demo" project compared to the linker step of the "SIP" project. They look identical to me except that the SIP build complains about undefined references. They are not undefined. Demo needs them too and the "nm" tool shows all of the so-called undefined references are in fact there in the Lib2 library.

I'm using Ubuntu 11.04 64bit.

Any suggestions?

// PROJECT DEMO
Building target: Demo
Invoking: GCC C Linker
gcc -L"/home/myname/projectdir/Lib1/Debug" -L"/home/myname/projectdir/Lib2/Debug" -o "Demo"  ./Callbacks.o ./CallbacksGrammar.o ./Setup.o ./SetupGrammar.o ./UdtLib.o ./UdtLibGrammar.o ./main.o   -lLib1 -lLib2
Finished building target: Demo


// PROJECT SIP
Building target: SIP
Invoking: GCC C Linker
gcc -L"/home/myname/projectdir/Lib1/Debug" -L"/home/myname/projectdir/Lib2/Debug" -o "SIP"  ./Messages.o ./SIPGrammar.o ./TortureTestTranslator.o ./main.o   -lLib1 -lLib2
/home/myname/projectdir/Lib2/Debug/libLib2.a(Utilities.o): In function `vDisplayOp':
/home/myname/projectdir/Lib2/Debug/../Utilities.c:607: undefined reference to `uiRNM'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:611: undefined reference to `uiUDT'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:614: undefined reference to `uiREP'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:620: undefined reference to `uiALT'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:626: undefined reference to `uiCAT'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:632: undefined reference to `uiAND'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:634: undefined reference to `uiNOT'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:636: undefined reference to `uiTRG'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:639: undefined reference to `uiTBS'
/home/myname/projectdir/Lib2/Debug/../Utilities.c:644: undefined reference to `uiTLS'
collect2: ld returned 1 exit status
make: *** [SIP] Error 1

---

