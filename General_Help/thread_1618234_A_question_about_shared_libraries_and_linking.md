---
title: "A question about shared libraries and linking"
date: 2010-11-10
forum: General Help
---

### Post by The average internet guy on 2010-11-10
I've recently started using Linux, and there is one thing that puzzles me a bit: The whole thing about shared and static libraries. As far as I know a program compiled with a shared library does not include this in its executable, but only knows how to interface it. A program compiled with a static library on the other hand includes the whole library in it's executable.

When I install an application from source, say hdf5, I simply run .configure --prefix=installdir and then make. However, when installing it in this way Ubuntu knows nothing about the path of the shared library directory in the hdf5 install location if I want to include it in a program. I guess I could manually write it into $LD_LIBRARY_PATH, but I read that this is evil and will make you a bad person :). How do I tell Ubuntu that I have a shared library in some directory that I want to be accessible?

Another related problem I have is a bit more specific. in my makefile I have the following line

```
HDFLIB=-L/opt/hdf5-1.6.10/lib -lhdf5 -lz -Wl,"-R /opt/hdf5-1.6.10/lib"
```If I break this statement down into it's components it basically says that I want to use the shared libraries in /opt/hdf5-1.6.10/lib when I compile my code. The -lhdf5 -lz I'm not so sure about. The -Wl,"-R /opt/hdf5-1.6.10/lib" tells the compiler to pass the argument -R /opt/hdf5-1.6.10/lib to the linker, which interprets this statement as: Make the shared library /opt/hdf5-1.6.10/lib available for the application during runtime. Is this correct? How come I still get a "error while loading shared libraries: libhdf5.so.0: cannot open shared object file: No such file or directory" when I try to run my program?

---

