---
title: "How to use an older GCC to compile"
date: 2009-07-14
forum: General Help
---

### Post by Techno_Fantsy on 2009-07-14
Hi everyone,
 
I'm new to ubuntu (and linux) and currently I have multiple programs that produce compiling errors when I tried to 'make' them, however, thier documentation showed that it doesn't produce errors when they use an older versions of GCC .. 
 
How can do that? Does this relate to do some changes on the 'config' file within the installation package?
 
Thank you in advance..
 
Techno

---

### Post by JohnnySage50307 on 2009-07-14
I'm not certain what you may be building, but it could have more to deal with the C standard that gcc is using, rather than which version of it.

Compilers typically don't change radically.  In my experience, however, when I first began setting up my Linux server, I noticed that my gcc was somehow missing the C99 standard.  I just updated GCC and everything works beautifully now.
 
All in all, I want to highly disuade you from using an older compiler.  The key motivation of updating a compiler is because security flaws are discovered and corrected.

---

### Post by JohnnySage50307 on 2009-07-14
While I'm thinking about it...are you running ./configure before making?  When I first started, that was my key issue.  Then I discovered alot of my programs were failing to make because I was missing a package, but the last few lines of the printout usually said what I was missing--I went out, found, and installed those and proceeded successfully.

---

### Post by Techno_Fantsy on 2009-07-14
Thank you John for your advice.. 
 
Would you mind to tell me how I do that, please?
I'm really new to this.. and I feel lost sometimes.. 
 
Do you mean by running ./configure that I just write:
 
[INDENT]make ./configure
 
[/INDENT]Sorry if these questions or notes are silly.. but I'll appriciate ny kinf of hints here..
 
Thaks again..
 
Techno

---

### Post by Techno_Fantsy on 2009-07-14
Ok guys.. this what I got from running ./configure to compile "Festival - Speech Tools"
-------------
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
------------

and when I run 'make' .. I got this .. 

------------
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
gcc -c -fno-implicit-templates -O3 -Wall -DSUPPORT_EDITLINE -I../include slib.cc
In file included from ../include/EST_String.h:50,
                 from ../include/siod.h:17,
                 from slib.cc:88:
../include/EST_iostream.h:52:25: error: iostream.h: No such file or directory
In file included from ../include/EST_String.h:53,
                 from ../include/siod.h:17,
                 from slib.cc:88:
../include/EST_Chunk.h:131: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:132: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:133: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:135: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:136: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:138: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:139: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:141: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_Chunk.h:141: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_Chunk.h:141: error: expected ‘;’ before ‘&’ token
../include/EST_Chunk.h:246: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_Chunk.h:246: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_Chunk.h:246: error: expected ‘;’ before ‘&’ token
In file included from ../include/siod.h:17,
                 from slib.cc:88:
../include/EST_String.h:640: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_String.h:640: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_String.h:640: error: expected ‘;’ before ‘&’ token
../include/EST_String.h: In member function ‘void EST_String::make_updatable()’:
../include/EST_String.h:253: error: no matching function for call to ‘make_updatable(EST_ChunkPtr&, int)’
../include/EST_String.h: In member function ‘EST_String EST_String::before(const char*, int) const’:
../include/EST_String.h:295: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘EST_String EST_String::at(const char*, int) const’:
../include/EST_String.h:311: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘EST_String EST_String::after(const char*, int) const’:
../include/EST_String.h:327: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘int EST_String::index(const char*, int) const’:
../include/EST_String.h:368: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘int EST_String::contains(const char*, int) const’:
../include/EST_String.h:381: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘int EST_String::gsub(const char*, const EST_String&)’:
../include/EST_String.h:407: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘int EST_String::gsub(const char*, const char*)’:
../include/EST_String.h:410: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘int EST_String::gsub(const EST_String&, const char*)’:
../include/EST_String.h:416: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: In member function ‘int EST_String::gsub(EST_Regex&, const char*)’:
../include/EST_String.h:423: error: ‘cerr’ was not declared in this scope
../include/EST_String.h: At global scope:
../include/EST_String.h:646: error: expected constructor, destructor, or type conversion before ‘&’ token
In file included from ../include/EST_String.h:648,
                 from ../include/siod.h:17,
                 from slib.cc:88:
../include/EST_Regex.h:118: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_Regex.h:118: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_Regex.h:118: error: expected ‘;’ before ‘&’ token
../include/EST_Regex.h:121: error: expected constructor, destructor, or type conversion before ‘&’ token
In file included from ../include/EST_string_aux.h:43,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TList.h:226: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_TList.h:226: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_TList.h:226: error: expected ‘;’ before ‘&’ token
../include/EST_TList.h:255: error: expected initializer before ‘&’ token
In file included from ../include/EST_types.h:44,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TVector.h:312: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_TVector.h:312: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_TVector.h:312: error: expected ‘;’ before ‘&’ token
../include/EST_TVector.h:327: error: expected initializer before ‘&’ token
In file included from ../include/EST_types.h:46,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TKVL.h:61: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_TKVL.h:61: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_TKVL.h:61: error: expected ‘;’ before ‘&’ token
../include/EST_TKVL.h:146: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_TKVL.h:146: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_TKVL.h:146: error: expected ‘;’ before ‘&’ token
../include/EST_TKVL.h:196: error: expected initializer before ‘&’ token
../include/EST_TKVL.h:199: error: expected initializer before ‘&’ token
In file included from ../include/EST_TSimpleMatrix.h:46,
                 from ../include/EST_FMatrix.h:44,
                 from ../include/EST_types.h:47,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TMatrix.h:310: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_TMatrix.h:310: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_TMatrix.h:310: error: expected ‘;’ before ‘&’ token
../include/EST_TMatrix.h:318: error: expected initializer before ‘&’ token
In file included from ../include/EST_FMatrix.h:47,
                 from ../include/EST_types.h:47,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_Val.h:244: error: ISO C++ forbids declaration of ‘ostream’ with no type
../include/EST_Val.h:244: error: ‘ostream’ is neither function nor member function; cannot be declared friend
../include/EST_Val.h:244: error: expected ‘;’ before ‘&’ token
../include/EST_Val.h:252: error: expected `;' before ‘}’ token
slib.cc: In function ‘int siod_register_user_type(const char*)’:
slib.cc:913: error: ‘cerr’ was not declared in this scope
slib.cc:914: error: ‘endl’ was not declared in this scope
slib.cc: In function ‘obj* user_gc(obj*)’:
slib.cc:1258: warning: suggest explicit braces to avoid ambiguous ‘else’
slib.cc: In function ‘obj* gc_status(obj*)’:
slib.cc:1278: warning: suggest explicit braces to avoid ambiguous ‘else’
slib.cc: In function ‘int flush_ws(gen_readio*, const char*)’:
slib.cc:1543: warning: suggest explicit braces to avoid ambiguous ‘else’
make[1]: *** [slib.o] Error 1
make: *** [siod] Error 2
-----------------

Does this there are some missing standards??
Or missing packages?


Techno

---

### Post by Techno_Fantsy on 2009-07-14
I found this on the internet:
[INDENT]"Note that Festival and EST can't be compiled with g++ 4, use g++ 3.X."
[/INDENT]So my question is how to specify the compiler version in the make command?

---

### Post by pedro_orange on 2009-07-14
> **Techno_Fantsy said:**
> I found this on the internet:
[INDENT]"Note that Festival and EST can't be compiled with g++ 4, use g++ 3.X."
[/INDENT]So my question is how to specify the compiler version in the make command?

The compiler version, is the version of the program you're compiling with. You need to remove the version you have now. And install an earlier one.

[http://gcc.gnu.org/releases.html](http://gcc.gnu.org/releases.html)

---

### Post by JohnnySage50307 on 2009-07-14
I see what's going on...Installing an older compiler *would* fix the problem, but for the wrong reasons...

You're missing C++ libraries it appears.  I would sugest just reinstalling or upgrading GCC.  The same thing happened to me when I first installed my Ubuntu Desktop and tried to install JDK.  When you reinstall GCC, it'll add and fix all of the missing or broken libraries.  Again, get the latest version.

---

### Post by bjdodo on 2009-07-14
Hi 

Here is an article about how to have 2 gcc versions in parallel:

[http://www.mjmwired.net/resources/mjm-fedora-gcc.html](http://www.mjmwired.net/resources/mjm-fedora-gcc.html)

But I think it is pretty difficult to achieve, especially for a guy who is new to Linux.

On the other hand probably fixing the build errors could be an easier path to take, you could get help from here & there. I do not have time now to go through this process with you, but as a start you could try this:

in ../include/EST_iostream.h

in line 52 (or 25?) most probably you have this: #include<iostream.h>

try to change this to #include<iostream>

and try to build again. If there is a reduction in the number of errors (and the compiler does not complain any more that it cannot find iostream or iostream.h) then you are one step ahead.

Good luck!

Jozsi

---

### Post by bjdodo on 2009-07-14
Oh forget my previous post for a moment! Ubuntu is a strange linux distro (for me)

Try to install the build essential package first.

sudo apt-get install build-essential

---

### Post by Techno_Fantsy on 2009-08-19
Thanks everyone.. 
 
I have upload the GCC 2.95.4 from the GCC website and install it along with all required libraries.
 
Then i remove the gcc symbolic link from gcc-4.3
and create another one to gcc-2.95.4
 
It works!
 
Anyhow.. The <iostream.h> error is still there.. I tried bjdodo solution as well but the error message changed from 
 
"iostream.h: no such file or directory"
 
to 
 
"iostream: no such file or directory"
 
**Is this related to the used standards in the GCC calls??? if so how can i access to it since the make is doing everything?? maybe through the makefile??**
 
I really can't figure it out.. 
would anyone help [frasturated]
 
Thanks alot..
 
TF

---

