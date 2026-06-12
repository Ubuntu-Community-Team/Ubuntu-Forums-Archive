---
title: "compiling qt with g++ include files"
date: 2006-03-26
forum: General Help
---

### Post by morpheus2485 on 2006-03-26
This is my first time trying to make a GUI program, and I am having problems compiling.  The problem is that g++ isn't checking the right folders for the include files, but I'm having a lot of troubble trying to figure out how to add them.

here is the output from "g++ -v temp.cpp"


Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
 /usr/lib/gcc/i486-linux-gnu/4.0.2/cc1plus -quiet -v -D_GNU_SOURCE temp.cpp -quiet -dumpbase temp.cpp -mtune=i486 -auxbase temp -version -o /tmp/cc4QNE8l.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/4.0.2
 /usr/include/c++/4.0.2/i486-linux-gnu
 /usr/include/c++/4.0.2/backward
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.0.2/include
 /usr/include
End of search list.
GNU C++ version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9) (i486-linux-gnu)
        compiled by GNU C version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9).
GGC heuristics: --param ggc-min-expand=47 --param ggc-min-heapsize=32089
temp.cpp:1:25: error: qapplication.h: No such file or directory
temp.cpp:2:24: error: qupshbutton.h: No such file or directory
temp.cpp: In function &#8216;int main(int, char**)&#8217;:
temp.cpp:7: error: &#8216;QApplication&#8217; was not declared in this scope
temp.cpp:7: error: expected `;' before &#8216;a&#8217;
temp.cpp:9: error: &#8216;QPushbutton&#8217; was not declared in this scope
temp.cpp:9: error: expected `;' before &#8216;hello&#8217;
temp.cpp:10: error: &#8216;hello&#8217; was not declared in this scope
temp.cpp:12: error: &#8216;a&#8217; was not declared in this scope



EDIT-----

It was a really silly solution.  The qt tutorial I was reading told me how to do it at the bootom of the page :-)

[http://doc.trolltech.com/3.3/tutorial1-01.html](http://doc.trolltech.com/3.3/tutorial1-01.html)

---

