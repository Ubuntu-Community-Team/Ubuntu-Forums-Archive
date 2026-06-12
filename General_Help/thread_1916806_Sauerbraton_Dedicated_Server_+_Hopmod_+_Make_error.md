---
title: "Sauerbraton Dedicated Server + Hopmod + Make error"
date: 2012-01-28
forum: General Help
---

### Post by morbidchimp on 2012-01-28
Just noticed an issue when installing hopmod for saur on ubuntu. The fix for it didn't come up easily on google search so thought I would post it here in case others were having the same problem. 

I'm currently seeing problem on 11.04 and 11.10 but it might effect other builds. 

Here is renewed installation instructions based on offical installion for hopmod

See Offical Installation Wiki here [http://hopmod.e-topic.info/index.php5?title=Installation]("http://hopmod.e-topic.info/index.php5?title=Installation")

When you come to using make or make install you may see the following error 85% through the process;

```

[ 85%] Building CXX object src/CMakeFiles/serverscripting.dir/hopmod/signals.cpp.o
Linking CXX executable luapp
libsauertools.a(utils.cpp.o): In function `timer::timer()':
utils.cpp:(.text+0x36d): undefined reference to `clock_gettime'
libsauertools.a(utils.cpp.o): In function `timer::usec_elapsed() const':
utils.cpp:(.text+0x38d): undefined reference to `clock_gettime'
collect2: ld returned 1 exit status
make[2]: *** [src/luapp] Error 1
make[1]: *** [src/CMakeFiles/luapp.dir/all] Error 2
make[1]: *** Waiting for unfinished jobs....
Linking CXX static library libserverscripting.a
[ 85%] Built target serverscripting
make: *** [all] Error 2
libsauertools.a(utils.cpp.o): In function `timer::timer()':
utils.cpp:(.text+0x36d): undefined reference to `clock_gettime'

```


If you do, apply this patch 

> 
Apply this patch:

Index: src/CMakeLists.txt
===================================================================
--- src/CMakeLists.txt	(revision 2487)
+++ src/CMakeLists.txt	(working copy)
@@ -46,6 +46,7 @@
     hopmod/net/address_prefix.cpp)
 
 add_library(sauertools STATIC ${SAUERTOOLS_SOURCES})
+target_link_libraries(sauertools -lrt)
 
 set(LUA_MODULES_SOURCES
     hopmod/lua/crypto.cpp


taken from here [http://code.google.com/p/hopmod/issues/detail?id=20]("http://code.google.com/p/hopmod/issues/detail?id=20")

or if your not sure how 
> 
go to the folder where you downloaded hopmod from the svn during installation (above)

you need to apply the patch to the file "CMakeLists.txt" so make sure you are in the folder where CMakeLists.txt is

make the patch file

nano patch.txt

paste the following in there

Apply this patch:


=== COPY AFTER THIS LINE ===
Index: src/CMakeLists.txt
===================================================================
--- src/CMakeLists.txt	(revision 2487)
+++ src/CMakeLists.txt	(working copy)
@@ -46,6 +46,7 @@
     hopmod/net/address_prefix.cpp)
 
 add_library(sauertools STATIC ${SAUERTOOLS_SOURCES})
+target_link_libraries(sauertools -lrt)
 
 set(LUA_MODULES_SOURCES
     hopmod/lua/crypto.cpp
=== END COPY AFTER THIS LINE ===

type

patch -p1 < patch.txt


then run 

make
make install

and continue on as per installation instructions



Best regards

---

