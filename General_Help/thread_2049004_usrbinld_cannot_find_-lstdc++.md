---
title: "/usr/bin/ld: cannot find -lstdc++"
date: 2012-08-27
forum: General Help
---

### Post by notxarb on 2012-08-27
While trying to build Boot to Gecko, I get the error message: 
/usr/bin/ld: cannot find -lstdc++

The full message is :
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/acp_intermediates/acp] Error 1
make: *** Waiting for unfinished jobs....
host Executable: adb (out/host/linux-x86/obj/EXECUTABLES/adb_intermediates/adb)
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/aidl_intermediates/aidl] Error 1
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/adb_intermediates/adb] Error 1
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/aapt] Error 1

real    0m13.269s
user    0m9.621s
sys    0m1.564s

> Build failed! <

What do I do?

---

### Post by qyot27 on 2012-08-27
Let me guess...cross-compiling for 32-bit using gcc-multilib?  I ran into the same issue when trying to compile FFmpeg some time ago.

The solution in such a case is to install g++-multilib.

---

### Post by notxarb on 2012-08-27
> **qyot27 said:**
> Let me guess...cross-compiling for 32-bit using gcc-multilib?  I ran into the same issue when trying to compile FFmpeg some time ago.

The solution in such a case is to install g++-multilib.

Okay, now it does this:

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/lib/libGLES_CM_translator.so] Error 1
make: *** Waiting for unfinished jobs....
external/icu4c/common/utrie2_builder.c: In function ‘utrie2_freeze_46’:
external/icu4c/common/utrie2_builder.c:1266:9: warning: comparison of unsigned expression < 0 is always false [-Wtype-limits]
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/lib/libEGL_translator.so] Error 1
external/icu4c/common/uloc_tag.c: In function ‘_ldmlKeyToBCP47’:
external/icu4c/common/uloc_tag.c:575:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
external/icu4c/common/uloc_tag.c: In function ‘_bcp47ToLDMLKey’:
external/icu4c/common/uloc_tag.c:637:19: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
external/icu4c/common/uloc_tag.c: In function ‘_ldmlTypeToBCP47’:
external/icu4c/common/uloc_tag.c:715:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
external/icu4c/common/uloc_tag.c:734:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
external/icu4c/common/uloc_tag.c: In function ‘_bcp47ToLDMLType’:
external/icu4c/common/uloc_tag.c:833:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
external/icu4c/common/uloc_tag.c:851:20: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]

real    1m5.780s
user    1m19.409s
sys    0m7.836s

> Build failed! <

---

