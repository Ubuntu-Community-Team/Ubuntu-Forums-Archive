---
title: "libmediastreamer.so and libortp.so are not properly linked"
date: 2011-10-28
forum: General Help
---

### Post by axeoth on 2011-10-28
Hello,

On Ubuntu Oneiric 64, I installed the libmediastreamer and libmediastreamer-dev packages.

Then, while compiling a program against mediastreamer (ie. using the -lmediastreamer flag), the linker returns an error:

>gcc test.c -lmediastreamer

/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libmediastreamer.so: undefined reference to symbol 'ortp_malloc'
 /usr/bin/ld: note: 'ortp_malloc' is defined in DSO /usr/lib/libortp.so.8 so try adding it to the linker command line
 /usr/lib/libortp.so.8: could not read symbols: Invalid operation
 collect2: ld returned 1 exit status

Adding -lortp flag does not resolve the problem.

This is a *very strange* error that I do not know how to interpret.

Apparently, the libmediastreamer.so library is corrupted.

Can someone guide me how to re-buil-it from the source?

I also reported this as a bug ([https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/876264](https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/876264)) but received no answer.

This completely broke my work on Oneiric. I miss Natty...

Thanks for the help.

---

### Post by axeoth on 2011-10-30
For information:

both libraries are in /usr/lib:

/usr/lib$ ls libmediastreamer* libortp*
libmediastreamer.so  libmediastreamer.so.0  libmediastreamer.so.0.0.0  libortp.so  libortp.so.8  libortp.so.8.0.0

and libmediastreamer.so depends on libortp.so:

/usr/lib$ ldd libmediastreamer.so.0.0.0 | grep libortp
	libortp.so.8 => /usr/lib/libortp.so.8 (0x00007f21646ed000)

And libmediastreamer.so really demands ortp_malloc symbol:

/usr/lib$ nm -D libmediastreamer.so.0.0.0 | grep malloc
                 U malloc
                 U ortp_malloc
                 U ortp_malloc0

while libortp.so really exports ortp_malloc symbol:

/usr/lib$ nm -D /usr/lib/libortp.so.8 | grep malloc
                 U malloc
0000000000007ea0 T ortp_malloc
0000000000007ed0 T ortp_malloc0

However, the compiler (linker) still complains about:

/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libmediastreamer.so: undefined reference to symbol 'ortp_malloc'
/usr/bin/ld: note: 'ortp_malloc' is defined in DSO /usr/lib/libortp.so.8 so try adding it to the linker command line
/usr/lib/libortp.so.8: could not read symbols: Invalid operation

Any news?

---

### Post by axeoth on 2011-10-30
Well, I finally succeeded to manage the problem. Below is how I did it, for further reference:

0. Even more first: here are the relevant links:
[http://lists.fedoraproject.org/pipermail/devel/2010-March/133601.html](http://lists.fedoraproject.org/pipermail/devel/2010-March/133601.html)
[https://fedoraproject.org/wiki/Features/ChangeInImplicitDSOLinking](https://fedoraproject.org/wiki/Features/ChangeInImplicitDSOLinking)
[https://fedoraproject.org/wiki/UnderstandingDSOLinkChange](https://fedoraproject.org/wiki/UnderstandingDSOLinkChange)
There is a change in the default behavior of the linker, that now does not *implicitely* links with NEEDED libraries, but requires to pass those libraries in explicit manner.

1. First of all, I was building the software using scons and the original command line as passed by scons to the environment was:

/build$ gcc -o program program.o -lm -lsndfile -lmediastreamer -lGL -lGLU -lglut -lIrrlicht -litpp libmsf_library.a libbas_library.a libtst_library.a
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libmediastreamer.so: undefined reference to symbol 'ortp_malloc'
/usr/bin/ld: note: 'ortp_malloc' is defined in DSO /usr/lib/libortp.so.8 so try adding it to the linker command line
/usr/lib/libortp.so.8: could not read symbols: Invalid operation
collect2: ld returned 1 exit status

The linker suggested "/usr/bin/ld: note: 'ortp_malloc' is defined in DSO /usr/lib/libortp.so.8 so try adding it to the linker command line"

2. However, if I added "-lortp" just after -lmediastreamer, it still complained (why? I cannot explain):

/build$ gcc -o program program.o -lm -lsndfile -lmediastreamer -lortp -lGL -lGLU -lglut -lIrrlicht -litpp libmsf_library.a libbas_library.a libtst_library.a
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libmediastreamer.so: undefined reference to symbol 'ortp_malloc'
/usr/bin/ld: note: 'ortp_malloc' is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libortp.so so try adding it to the linker command line
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libortp.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status

3. By hazard, I added the litigious "-lortp" last in the command line, after all the files:

/build$ gcc -o program program.o -lm -lsndfile -lmediastreamer -lGL -lGLU -lglut -lIrrlicht -litpp libmsf_library.a libbas_library.a libtst_library.a -lortp
libmsf_library.a(msf_sinker_glutdisplay.o): In function `glut_animate':
/home/user/eclipse-workspace/program/msf_sinker_glutdisplay.c:18: undefined reference to `glutPostRedisplay'
[...skipped...]
collect2: ld returned 1 exit status

So, now IT WORKED! I mean, it found the "ortp_malloc" symbol declared in the "libortp.so" library, but started complaining about not finding various glut, GLU and GL functions (although the libraries are plassed, but *before* the files).

4. Finally, I decided to move all libraries *at the end* of the command line:

/build$ gcc -o program program.o libmsf_library.a libbas_library.a libtst_library.a -lortp -lm -lsndfile -lmediastreamer -lGL -lGLU -lglut -lIrrlicht -litpp

and, now, the compilation went flawless.

Now, the real question remains how to persuade scons to put libraries at the end, but that is outside this topic.

I will mark this thread as solved.

---

### Post by small4136 on 2012-08-28
H&#305;,
I have the similar problem, when I try to build linphone o I got these errors;


c-------r@c-------r:~/Desktop/src/libjingle/talk$ 
/home/c---------r/Desktop/src/swtoolkit/hammer.sh
scons: Reading SConscript files ...

scons: warning: No version of Visual Studio compiler found - C/C++ compilers most likely not set correctly
File "/home/c-------r/Desktop/src/swtoolkit/site_scons/site_tools/target_platform_windows.py", line 283, in generate
scons: done reading SConscript files.
scons: Building targets ...
scons: `all_libraries' is up to date.
________Linking build/dbg/obj/call
/usr/bin/ld: skipping incompatible /usr/lib/libmediastreamer.so when searching for -lmediastreamer
/usr/bin/ld: cannot find -lmediastreamer
collect2: ld returned 1 exit status
scons: *** [build/dbg/obj/call] Error 1
scons: building terminated because of errors.

Can u tell me how can I solve that problem...

---

