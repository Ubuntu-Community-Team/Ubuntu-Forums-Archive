---
title: "Unable to find X libraries when configuring firefox with intel C compiler"
date: 2010-04-05
forum: General Help
---

### Post by mononom on 2010-04-05
I'm using Karmic 64bit.

I tried to build firefox with PGO using Intel C Compiler (icc), but, configure gave this error message.

```
configure: error:  Could not find the following X libraries:  -lX11 -lXext -lXt 
*** Fix above errors and then restart with               "make -f client.mk build"
```

When I tried it using gcc, there's no error msg. 
What can I do?

My .mozconfig file is...
```
export CC=icc
export CFLAGS="-ipo -xSSE3 -fbuiltin-func -axSSE3 -no-prec-div -static -finline -finline-functions -g0 -L/usr/lib -L/usr/lib32 -L/usr/local/lib -L/usr/local/lib32 -L/lib -L/lib32"
export CXX=icc
export CXXFLAGS="$CFLAGS"

ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_MAKE_FLAGS=-j
mk_add_options MOZ_OBJDIR=/home/mono/mozilla-1.9.2/obj-@CONFIG_GUESS@
mk_add_options PROFILE_GEN_SCRIPT=./run-firefox.sh



ac_add_options --enable-optimize=-O3
ac_add_options --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-gnomeui
ac_add_options --enable-profile-guided-optimization
ac_add_options --disable-crashreporter
ac_add_options --enable-safe-browsing
ac_add_options --enable-faststart
ac_add_options --disable-necko-wifi
```

and icc is installed at "/opt/intel/Compiler/11.1/"

search path of gcc is 
```
install: /usr/lib/gcc/x86_64-linux-gnu/4.4.1/
programs: =/usr/lib/gcc/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/libexec/gcc/x86_64-linux-gnu/4.4.1/:/usr/libexec/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../x86_64-linux-gnu/bin/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../x86_64-linux-gnu/bin/
libraries: =/opt/intel/Compiler/11.1/069/lib/intel64/x86_64-linux-gnu/4.4.1/:/opt/intel/Compiler/11.1/069/lib/intel64/../lib/:/opt/intel/Compiler/11.1/069/ipp/em64t/lib/x86_64-linux-gnu/4.4.1/:/opt/intel/Compiler/11.1/069/ipp/em64t/lib/../lib/:/opt/intel/Compiler/11.1/069/mkl/lib/em64t/x86_64-linux-gnu/4.4.1/:/opt/intel/Compiler/11.1/069/mkl/lib/em64t/../lib/:/opt/intel/Compiler/11.1/069/tbb/intel64/cc4.1.0_libc2.4_kernel2.6.16.21/lib/x86_64-linux-gnu/4.4.1/:/opt/intel/Compiler/11.1/069/tbb/intel64/cc4.1.0_libc2.4_kernel2.6.16.21/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../x86_64-linux-gnu/lib/x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../x86_64-linux-gnu/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../x86_64-linux-gnu/4.4.1/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/:/lib/x86_64-linux-gnu/4.4.1/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/4.4.1/:/usr/lib/../lib/:/usr/lib/x86_64-linux-gnu/x86_64-linux-gnu/4.4.1/:/usr/lib/x86_64-linux-gnu/../lib/:/opt/intel/Compiler/11.1/069/lib/intel64/:/opt/intel/Compiler/11.1/069/ipp/em64t/lib/:/opt/intel/Compiler/11.1/069/mkl/lib/em64t/:/opt/intel/Compiler/11.1/069/tbb/intel64/cc4.1.0_libc2.4_kernel2.6.16.21/lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../x86_64-linux-gnu/lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../:/lib/:/usr/lib/:/usr/lib/x86_64-linux-gnu/
```

and search path of icc is 
```
install: /opt/intel/Compiler/11.1/069/bin/intel64
programs: =/opt/intel/Compiler/11.1/069/bin/intel64::/opt/intel/Compiler/11.1/069/bin/intel64:.:/home/mono/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/depot_tools:/opt/depot_tools
libraries: =/opt/intel/Compiler/11.1/069/lib/intel64:/usr/lib64
```


how to set search directories of icc?
i think search path of icc causes an above problem...


Sorry for poor english.

---

### Post by mononom on 2010-04-06
nobody knows? TT

---

### Post by lovinglinux on 2010-04-06
> **mononom said:**
> nobody knows? TT

Is not considered polite to bump your thread so fast. Please wait at least 24 hours to ask again, if you don't receive any replies.

Keep in mind that this is a very specific question, so perhaps you would have a better chance of getting a response at the [Packaging and Compiling Programs](http://ubuntuforums.org/forumdisplay.php?f=44) forum.

You can click on the "Report Abuse" button and ask a moderator to move it there.

---

