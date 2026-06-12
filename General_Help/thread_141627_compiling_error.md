---
title: "compiling error"
date: 2006-03-08
forum: General Help
---

### Post by Angry penguin on 2006-03-08
I am trying to compile a program (festvox) for text-to-speech in breezy for the program "mister house" , here is the output.

[B]rlozier@blazingfast:~/speech/speech_tools$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for ar... (cached) ar
checking whether byte ordering is bigendian... (cached) no
checking for tputs in -ltermcap... (cached) no
checking for tputs in -lncurses... (cached) no
creating ./config.status
creating config/config
rlozier@blazingfast:~/speech/speech_tools$ make
Check system type
Remake modincludes.inc
        NATIVE_AUDIO
                ok
        EDITLINE
                config/modules/editline.mak
        SIOD
                siod/siod.mak
        WAGON
                stats/wagon/wagon.mak
        SCFG
                grammar/scfg/scfg.mak
        WFST
                grammar/wfst/wfst.mak
        OLS
                stats/ols.mak
        RXP
                rxp/rxp.mak
        LINUX16_AUDIO
                config/modules/linux16_audio.mak
Making in directory ./siod ...
gcc -c -fno-implicit-templates -O3 -Wall -DSUPPORT_EDITLINE -I../include slib.ccIn file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from ../include/EST_iostream.h:52,
                 from ../include/EST_String.h:50,
                 from ../include/siod.h:17,
                 from slib.cc:88:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
../include/EST_Chunk.h:131: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:132: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:133: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:135: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:136: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:138: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:139: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_TList.h:226: warning: friend declaration ‘std::ostream& 
../include/EST_TList.h:226: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TList<T>&)’ declares a non-template function
../include/EST_TList.h:226: warning: (if this is not what you intended, make sure the function template has already been declared and add <> after the function name here) -Wno-non-template-friend disables this warning
../include/EST_TVector.h:312: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TVector<T>&)’ declares a non-template function
../include/EST_TKVL.h:61: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TKVI<K, V>&)’ declares a non-template function
../include/EST_TKVL.h:146: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TKVL<K, V>&)’ declares a non-template function
../include/EST_TMatrix.h:310: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TMatrix<T>&)’ declares a non-template function
make[1]: *** [slib.o] Error 1
make: *** [siod] Error 2
[/B]

any idea why this isnt working?

---

### Post by glug101 on 2006-03-08
If I had to make a guesse, I'd say that your slib install is borked.  Try reinstalling it through synaptic.  If that doesn't fix it (or it's not listed), try downloading a copy of it from the internet and compile it also.

I've personally never heard of this package before, but I found a little documentation on it in Google (the repository of all knowledge ;) )

---

### Post by Angry penguin on 2006-03-08
i have managed to fix that problem by apt-getting the package instead of compiling, now i have a new problem.

I am trying to install freetts, after saying yes to the agreement, here is the output.

[B]x - creating lock directory
x - extracting jsapi.jar (binary)
./jsapi.sh: line 257: uudecode: command not found
restore of jsapi.jar failed
jsapi.jar: MD5 check failed
[/B]

thanks,

---

### Post by Angry penguin on 2006-03-09
after googling for a while i found the solution: I had to install sharutils because uudecode is part of that package, that fixed this problem.

Now for my last trick, I need to specify the classpath for a demo, i have freetts installed now i am trying to build a demo to see if it works. This is the page i am using for instructions.

[http://freetts.sourceforge.net/docs/index.php#run_demo](http://freetts.sourceforge.net/docs/index.php#run_demo)

could someone point me to a good howto for specifying classpaths?

---

