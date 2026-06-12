---
title: "cannot find -lstdc++"
date: 2010-11-04
forum: General Help
---

### Post by dinkyverma279 on 2010-11-04
Hi,

I am building ANDROID sdk using ubuntu 9.10. I have 64 bit version, but when I am building, i am getting the build error:

I even installed libstdc++6-4.4-dev package. But it did not work. I am getting following build error:

host Executable: acp (out/host/linux-x86/obj/EXECUTABLES/acp_intermediates/acp)
host Executable: aapt (out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/aapt)
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
/usr/bin/ld: skipping incompatible /usr/lib/../lib/librt.so when searching for -lrt
/usr/bin/ld: skipping incompatible /usr/lib/../lib/librt.a when searching for -lrt
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libz.a when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.a when searching for -lz
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status


Can somebody point me the right package for ubuntu 64 bit?

regards
dinky

---

### Post by mc4man on 2010-11-04
Have not a clue about ANDROID  but I'd probably install ia32-libs (which should also pull in lib32stdc++6

---

