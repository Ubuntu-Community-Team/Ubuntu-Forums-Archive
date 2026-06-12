---
title: "Installing CIL-1.3.7"
date: 2009-08-21
forum: General Help
---

### Post by newport_j on 2009-08-21
I am having problems running CIL-1.3.7. The CIL installation instructions say to download CIL first (obviously) onto the Desktop. The instuctions then say to unzip  and untar the package with this command:

tar xvfz cil-1.3.7.tar.gz.

This works fine, though the directory created is not cil, but   cil-1.3.7. Anyway the next three steps come in sequence and follow like this:

Now I have Ocaml 3-0.09.3 installed. It works with the CIL software. If the current version (Ocaml-3.0.11) is installed running these three commands below will create a warning that CIL cannot run with this latest version of Ocaml, Ocaml-3-11.. Uninstall it and reinstall 3.09. I installed 3.09.3. I believe the problem is not Ocaml. 

 
./configure
make
make quicktest 

Now when running these three commands. ./configure works fine-no problem here. using the next command make is a problem. It runs for a while and them it fails with the error:

Compiling C file ocamlutil/perfcount.c 
Linking native code obj/x86_LINUX/cilly.asm.exe 
Cannot find file std_exit.cmx
make[1]: *** [obj/x86_LINUX/cilly.asm.exe] Error 2
make[1]: Leaving directory `/home/james/Desktop/cil-1.3.7'
make: *** [setup] Error 2

The file cilly.asm.exe is not compiled. Now strangely when I run the third command:

make quicktest 


It runs fine with everything successful! I do not understand. The error says it cannot find

std_exit.cmx 

in the obj.x86_LINUX/ directory. It is not there.  But when I add it from Ocaml-3.09.3, it still says it cannot find it. I have added it and it cannot find it.!

So what is happening here. 

Any help appreciated.

Respectfully,

newport_j

---

