---
title: "Sphere Game Dev."
date: 2010-05-02
forum: General Help
---

### Post by Nick43092 on 2010-05-02
I'm trying to install Sphere Game Development environment, but in order to use it, i need to build corona libraries from source - version 1.0.2. Unfortunately, I get errors whenever I try to use the make command. I'm using ubuntu 9.04 x64, and I grabbed the only unix package from the corona website. any help would be greatly appreciated. 

the errors:
```

make  all-recursive
make[1]: Entering directory `/home/nick/Desktop/corona-1.0.2'
Making all in src
make[2]: Entering directory `/home/nick/Desktop/corona-1.0.2/src'
Making all in libungif-4.1.0
make[3]: Entering directory `/home/nick/Desktop/corona-1.0.2/src/libungif-4.1.0'
if /bin/bash ../../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"corona\" -DVERSION=\"1.0.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I.     -g -O2 -Wall -Wno-non-virtual-dtor -MT dgif_lib.lo -MD -MP -MF ".deps/dgif_lib.Tpo" \
      -c -o dgif_lib.lo `test -f 'dgif_lib.c' || echo './'`dgif_lib.c; \
    then mv -f ".deps/dgif_lib.Tpo" ".deps/dgif_lib.Plo"; \
    else rm -f ".deps/dgif_lib.Tpo"; exit 1; \
    fi
rm -f .libs/dgif_lib.lo
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"corona\" -DVERSION=\"1.0.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -g -O2 -Wall -Wno-non-virtual-dtor -MT dgif_lib.lo -MD -MP -MF .deps/dgif_lib.Tpo -c dgif_lib.c  -fPIC -DPIC -o .libs/dgif_lib.lo
cc1: warning: command line option "-Wno-non-virtual-dtor" is valid for C++/ObjC++ but not for C
dgif_lib.c: In function 'DGifOpenFileHandle':
dgif_lib.c:122: warning: pointer targets in passing argument 2 of '((struct GifFilePrivateType *)GifFile->Private)->Read' differ in signedness
dgif_lib.c: In function 'DGifOpen':
dgif_lib.c:186: warning: pointer targets in passing argument 2 of '((struct GifFilePrivateType *)GifFile->Private)->Read' differ in signedness
dgif_lib.c: In function 'DGifSlurp':
dgif_lib.c:945: warning: pointer targets in assignment differ in signedness
dgif_lib.c:947: warning: pointer targets in passing argument 2 of 'DGifGetLine' differ in signedness
dgif_lib.c:974: warning: pointer targets in passing argument 3 of 'AddExtensionBlock' differ in signedness
dgif_lib.c: At top level:
gif_lib_private.h:55: warning: 'VersionStr' defined but not used
Assembler messages:
Fatal error: can't create .libs/dgif_lib.lo: Permission denied
make[3]: *** [dgif_lib.lo] Error 1
make[3]: Leaving directory `/home/nick/Desktop/corona-1.0.2/src/libungif-4.1.0'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nick/Desktop/corona-1.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nick/Desktop/corona-1.0.2'
make: *** [all] Error 2
nick@ubuntu:~/Desktop/corona-1.0.2$ sudo nautilus
[sudo] password for nick: 
Initializing nautilus-dropbox 0.6.1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:3291): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///

(nautilus:3291): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:3291): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time

```

---

### Post by koanhead on 2010-05-02
It looks like make failed because it couldn't mkdir into that subdirectory. It's within your $HOME, so you should have that permission unless you have changed the permission for ~/src. 
Can you mkdir that directory manually? If so, does that clear up the error, or is make not allowed to write there?
What does ls -la say about the parent directory?

---

