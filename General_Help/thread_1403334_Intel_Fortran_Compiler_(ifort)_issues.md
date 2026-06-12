---
title: "Intel Fortran Compiler (ifort) issues"
date: 2010-02-10
forum: General Help
---

### Post by tuwe on 2010-02-10
Hello,

i have managed to install the intel fortran compiler by following this howto: [http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

However, the ifort executable can't be found unless I add ```
source /opt/intel/Compiler/11.1/064/bin/ifortvars.sh intel64
``` to my ~/.bashrc

Afterwards, the famous helloworld example works.

I am trying to use Ansys with User Programmable Features. To achieve this, I have to edit an UPF which is normally a fortran routine to my needs, save it to a custom location (somewhere inside my home directory) and call an ansys script which does the dirty work.
However, it gives errors like these:
```
 Linking ansyscust.e120  - please wait

 FAILURE LINKING ansyscust.e120.  See file link.err.
```
```
uwe@switchbs360:~$ cat link.err 
ld: cannot find -lXm
```

A look inside /usr/lib gives
```
uwe@switchbs360:~$ ls -la /usr/lib/libXm.*
lrwxrwxrwx 1 root root      14 2010-01-27 10:05 /usr/lib/libXm.so.3 -> libXm.so.3.0.2
-rw-r--r-- 1 root root 2842688 2008-11-10 22:41 /usr/lib/libXm.so.3.0.2
```

I can work around this error by linking /usr/lib/libXm.so.3.0.2 to /usr/lib/libXm.so, but this does not seem to be the correct way as i only end up with the next very similar error.

Also, $LD_LIBRARY_PATH is empty before sourcing the aforementioned shell script and becomes ```
uwe@switchbs360:~$ echo $LD_LIBRARY_PATH
/opt/intel/Compiler/11.1/064/lib/intel64:/opt/intel/Compiler/11.1/064/mkl/lib/em64t
``` afterwards.

It seems as if the regular libraries are missing from the path? What do I have to do to have ifort find the needed libraries?

Thanks in advance

---

### Post by tuwe on 2010-02-10
Ok actually the required dev files for compiling ansys were missing. The issue is resolved by installing them.

```
sudo apt-get install libxmu-dev libxt-dev libxi-dev libxp-dev libmotif-dev
```

:popcorn:

---

