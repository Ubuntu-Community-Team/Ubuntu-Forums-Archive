---
title: "Compiling pdf2xml on Ubuntu 10.10"
date: 2010-11-13
forum: General Help
---

### Post by MISIIM on 2010-11-13
I'm not sure how much of a difference this makes, but I am running Ubuntu 10.10 64-bit.

Anyway, I am trying to compile pdf2xml ([http://www.mobipocket.com/dev/pdf2xml/](http://www.mobipocket.com/dev/pdf2xml/)), but it is getting syntax errors. I'm not sure what to do about it.

I've been trying to use this command. I also tried it with g++ instead of gcc. I'd really appreciate any help. 

gcc -o pdf2xml pdf2xml.cpp ./xpdf/goo/gmem.c ./image/zlib/*.c ./image/png/*.c ./xpdf/fofi/*.cc ./xpdf/goo/*.cc -I ./xpdf/ -I ./xpdf/fofi/ -I ./xpdf/goo/ -I ./xpdf/xpdf/ -I ./image/zlib/ -I ./image/png -lm

```
pdf2xml.cpp: In member function ‘bool XmlOutput::load_from_pdf(GString&, GString&)’:
pdf2xml.cpp:497: warning: deprecated conversion from string constant to ‘char*’
pdf2xml.cpp: In member function ‘virtual void MbpOutputDev::drawString(GfxState*, GString*)’:
pdf2xml.cpp:823: warning: deprecated conversion from string constant to ‘char*’
...snip...
./xpdf/fofi/FoFiType1C.cc:943: warning: deprecated conversion from string constant to ‘char*’
./xpdf/fofi/FoFiType1C.cc: In member function ‘void FoFiType1C::eexecCvtGlyph(Type1CEexecBuf*, char*, int, int, Type1CIndex*, Type1CPrivateDict*)’:
./xpdf/fofi/FoFiType1C.cc:963: warning: deprecated conversion from string constant to ‘char*’
./xpdf/fofi/FoFiType1C.cc: In member function ‘void FoFiType1C::eexecWrite(Type1CEexecBuf*, char*)’:
./xpdf/fofi/FoFiType1C.cc:1685: warning: deprecated conversion from string constant to ‘char*’
./xpdf/fofi/FoFiType1C.cc: In member function ‘void FoFiType1C::eexecWriteCharstring(Type1CEexecBuf*, Guchar*, int)’:
./xpdf/fofi/FoFiType1C.cc:1708: warning: deprecated conversion from string constant to ‘char*’
In file included from ./xpdf/goo/gfile.cc:31:
./xpdf/goo/gfile.h:131: error: ISO C++ forbids declaration of ‘DIR’ with no type
./xpdf/goo/gfile.h:131: error: expected ‘;’ before ‘*’ token
./xpdf/goo/gfile.cc: In constructor ‘GDir::GDir(char*, GBool)’:
./xpdf/goo/gfile.cc:618: error: ‘dir’ was not declared in this scope
./xpdf/goo/gfile.cc:618: error: ‘opendir’ was not declared in this scope
./xpdf/goo/gfile.cc: In destructor ‘GDir::~GDir()’:
./xpdf/goo/gfile.cc:635: error: ‘dir’ was not declared in this scope
./xpdf/goo/gfile.cc:636: error: ‘closedir’ was not declared in this scope
./xpdf/goo/gfile.cc: In member function ‘GDirEntry* GDir::getNextEntry()’:
./xpdf/goo/gfile.cc:672: error: ‘dir’ was not declared in this scope
./xpdf/goo/gfile.cc:673: error: ‘readdir’ was not declared in this scope
./xpdf/goo/gfile.cc:674: error: invalid use of incomplete type ‘struct direct’
./xpdf/goo/gfile.cc:670: error: forward declaration of ‘struct direct’
./xpdf/goo/gfile.cc:678: error: invalid use of incomplete type ‘struct direct’
./xpdf/goo/gfile.cc:670: error: forward declaration of ‘struct direct’
./xpdf/goo/gfile.cc: In member function ‘void GDir::rewind()’:
./xpdf/goo/gfile.cc:699: error: ‘dir’ was not declared in this scope
./xpdf/goo/gfile.cc:700: error: ‘rewinddir’ was not declared in this scope

```

---

### Post by MISIIM on 2010-11-13
I've made some progress after searching the web for some obscure words.

It appears the best way to get it is from here: [https://launchpad.net/pdf2xml](https://launchpad.net/pdf2xml)

I needed to install some packages.

libpng12-dev
libpoppler-cpp-dev

I'm not sure that the C++ library is needed, but installing it works. The only problem is it does not output any images and does not reference them in the xml file. Sadly having images is very important for me. I will post at the launchpad page about that.

---

