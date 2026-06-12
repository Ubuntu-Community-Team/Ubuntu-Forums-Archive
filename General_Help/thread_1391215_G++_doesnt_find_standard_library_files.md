---
title: "G++ doesnt find standard library files"
date: 2010-01-26
forum: General Help
---

### Post by Le-Froid on 2010-01-26
When trying to compile any program lately i kept on getting weird errors.

I made a hello world file to see if it can compile and i found this error:

```

$ g++ test.cpp -o test                                  
test.cpp:1:20: error: iostream: No such file or directory
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:5: error: &#8216;cout&#8217; is not a member of &#8216;std&#8217;

```

there wasn't any errors in the code, it just said
```

  #include <iostream>
   
   int main()
   {
   std::cout << "Hi";
   }

```

I looked around /usr/include and noticed the c++ include files are under "/usr/include/c++/4.4". Does anyone know why g++ won't find this directory?

edit: g++ -v also reports this 
```

Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix **--with-gxx-include-dir=/usr/include/c++/4.4** --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu

``` so it was built to work with the /usr/include/c++/4.4 dir, but looks in /usr/include

---

