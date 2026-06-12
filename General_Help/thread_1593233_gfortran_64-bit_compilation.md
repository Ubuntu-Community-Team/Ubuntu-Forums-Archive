---
title: "gfortran 64-bit compilation?"
date: 2010-10-11
forum: General Help
---

### Post by mwparis on 2010-10-11
I have read the FAQ in the programming forum but am posting here because this is really an elementary, beginner's-type of question.

I am attempting to upgrade 32-bit legacy fortran code to 64-bit.

Here is my system uname: ```
$ uname -a
Linux assa79 2.6.31-22-server #65-Ubuntu SMP Thu Sep 16 16:33:54 UTC 2010 x86_64 GNU/Linux
```

It appears to be 64-bit. Question 1) Is this right?

I have successfully compiled the legacy fortran code using gfortran. Here is my gfortran version:

```
$ gfortran -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 

```

It also appears to be 64-bit. Question 2) Is this right?

The compilation links a lot of libraries (system and user written). I have not done comprehensive testing of the code, but it appears to work.

Here is the command line compilation command:
```
gfortran -o $exe -O3 -w -Wno-globals -fno-automatic -fno-second-underscore $fo  $lz $so $gp -lpng -lgd -lm -lXt -lX11 -lg2c
```

Question 3) How can I be sure that those system libraries are also 64-bit? Would the linker complain if they weren't? Or is it possible that these libs could be linked despite being 32-bit?

Thanks in advance.

---

### Post by mwparis on 2010-10-12
Have I posted this in an unacceptable location? Or is it that no one knows? (I'd believe "no one cares" before "no one knows.")

---

### Post by mwparis on 2010-10-14
Maybe I don't get any replies because I don't have a cool username.

---

### Post by anglican on 2010-10-14
> **mwparis said:**
> Maybe I don't get any replies because I don't have a cool username.I doubt that's the reason.:wink:
If you're unsure you can always try:
```
file <name of executable>

```which will tell you that your executable is 64-bit then use ldd to see which shared libraries it needs and check them with "file" too. But from the looks of your system and compiler it will be all 64-bit.

H

---

### Post by mwparis on 2010-10-14
> **anglican said:**
> I doubt that's the reason.:wink:

Yeah, but I still might change my username to something like 'Vimpaler' or 'FarTron.'

Anyhow, thanks. That's exactly what I was looking for. Here dem beans.

---

