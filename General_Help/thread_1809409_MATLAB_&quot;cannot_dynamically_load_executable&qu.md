---
title: "MATLAB &quot;cannot dynamically load executable&quot; and the &quot;-shared&quot; g++ linking flag"
date: 2011-07-21
forum: General Help
---

### Post by noobinabox on 2011-07-21
I am currently creating a MEX wrapper for a C++ program which utilizes a Makefile to compile and link.
I am running everything on Linux Ubuntu 10.04, with the g++-4.3 compiler.

My  short-term goal is to have it compile and link all libraries and source  code with the MEX options (found when performing mex -v) and then have  it run, even if it did not input or output any values.

**Currently, I  stand at a point where including the "-shared" flag in the final  linking command will result in the following error:**
```
/usr/bin/ld: ./src/radsrc/src/radsrc.a(dbmanager.o): relocation R_X86_64_32S against `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage' can not be used when making a shared object; recompile with -fPIC
./src/radsrc/src/radsrc.a: could not read symbols: Bad value
```[B]

If I exclude the "-shared" option, I successfully compile and  link with the makefile, but on running the MEX, I get the following  error in the Matlab Console:[/B]
```
??? Invalid MEX-file '/home/[PATH TO DIRECTORY]/xpassv3/xpass.mexa64': /home/[PATH TO DIRECTORY]/xpassv3/xpass.mexa64:
cannot dynamically load executable
```Can anyone give me advice on how to continue? I suspect leaving out the -shared option results in problems with  dynamically loading the executable, however I don't know how to resolve  the "recompile with -fPIC" since I've already tried including -fPIC in  the g++ options.
Any help resolving this would be greatly appreciated.

Respectfully,
Noobinabox

---

