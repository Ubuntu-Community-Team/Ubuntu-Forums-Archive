---
title: "trouble installing moses"
date: 2009-10-15
forum: General Help
---

### Post by s.adarsh on 2009-10-15
Hi all,

I am trying to install moses in a server (where i am not a root).
Right now I am having trouble installing irstlm, these are steps to be done
./configure
make
make install

configure results like this:
> 
...
checking for cos in -lm... yes
checking for gzopen in -lz... **no**
checking how to run the C preprocessor... gcc -E
...


while running make:
> 
...
gzfilebuf.h:8:18: error: zlib.h: No such file or directory
gzfilebuf.h:78: error: ‘gzFile’ does not name a type
gzfilebuf.h: In constructor ‘gzfilebuf::gzfilebuf(const char*)’:
...


I've tried "locate zlib.h" and got location as "/usr/include/linux".
I've then tried to edit Makefile and set CXXFlags to "-I/usr/include/linux" and also in irstlm/src/Makefile
Now I am getting new set of errors...
> 
....
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: In member function ‘typename std::basic_istream<_CharT, _Traits>::int_type std::basic_istream<_CharT, _Traits>::get()’:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:449: error: ‘_M_gcount’ was not declared in this scope
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(_CharT&)’:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:478: error: ‘_M_gcount’ was not declared in this scope
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:508: error: ‘streamsize’ has not been declared
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(_CharT*, int, _CharT)’:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:510: error: ‘_M_gcount’ was not declared in this scope
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(std::basic_streambuf<_CharT, _Traits>&, _CharT)’:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:552: error: ‘_M_gcount’ was not declared in this scope
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:589: error: ‘streamsize’ has not been declared
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(_CharT*, int, _CharT)’:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:591: error: ‘_M_gcount’ was not declared in this scope
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore()’:
....


I have already installed moses in my laptop and everything installed fine.

Someone please help me solve this problem

Thank you

Adarsh

---

### Post by justleen on 2009-10-15
YOu not root, so the make install will most likely fail, unless you added configure parameters (normally make install will try to install to system folders, which you dont have access to).

Secondly, the configure is already spitting out a missing library. Since you are not root, you can't just install it. You'd have install that inside your dir where you have write access, then point the configure of moses to that dir for gzlib..

---

### Post by s.adarsh on 2009-10-15
I am installing it in my home folder. And as I have already pointed out, I did change CXXFLAGS to include zlib.h file. But now I am getting different errors. I don't know if the change I made triggered it or something else...

---

### Post by justleen on 2009-10-15
Try to complete the configure without errors, then run a make, without a make install. That should at least give you the binary executables.

---

