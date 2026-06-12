---
title: "include files in QT creator"
date: 2009-12-24
forum: General Help
---

### Post by msbealo on 2009-12-24
Hi,

I'm not sure if this the right place to ask, if not, please direct.

My question is a general compiler/QT question which has come about because I'm trying to get FANN (neural networking library) working with QT. My problem is this:

In the example file xor_sample.cpp, it says

```
#include "floatfann.h"
#include "../src/floatfann.c"
#include "fann_cpp.h"

```

The include files are kept in /home/user_name/ANN/fann/fann-2.1.0/src and /home/user_name/ANN/fann/fann-2.1.0/src/include.

When I compile this xor_sample.cpp with g++, to allow g++ to find the include files, I use the command:

```
g++ -I../src/ -I../src/include/ xor_sample.cpp -o xor_sample

```

If I wrote a similar program in QT Creator, how do I tell it to look in the above directories to find the required include files?

Thanks,

msbealo

---

### Post by nikhilbhardwaj on 2009-12-24
add these files to your project

---

### Post by msbealo on 2009-12-24
nikhilbhardwaj,

Thanks. That gets around the files that I specifically include, but how do I deal with the long list of files that are included in these files? Do I have to add them ALL to the project? There must be a way for me to tell QT Creator to look in a certain directory for additional include files?

msbealo

---

### Post by msbealo on 2009-12-24
Alternatively, seeing as QT Creator uses g++, how might I configure g++ to look in an directory for additional include files?

---

### Post by msbealo on 2009-12-24
I thought that something like this might help. 

I've added in the INCLUDEPATH variable into the project file. It has some effect, but it's still not working properly.

```
# -------------------------------------------------
# Project created by QtCreator 2009-12-24T08:44:02
# -------------------------------------------------
QT -= gui
TARGET = xor_sample_QT
CONFIG += console
CONFIG -= app_bundle
TEMPLATE = app
INCLUDEPATH = /home/msbealo/ANN/fann/fann-2.1.0/src/ /home/msbealo/ANN/fann/fann-2.1.0/src/include/
SOURCES += main.cpp \
    xor_sample.cpp \
```

Any suggestions?

msbealo

---

### Post by msbealo on 2009-12-26
Is anyone willing to have a go at this?

---

### Post by msbealo on 2009-12-27
Ok, I've come some way to sorting this out, but it's still not working.

Originally the problem I was having was that the C++ wrapper for fann was bring up errors when I tried to compile in either g++ or QT Creator. I fixed the problem with g++ by adding the include path of the local copies of the headers. I've now realised that this was necessary because the debian package of libfann1-dev does not include the c++ wrapper files (which come as standard within the release version) and therefore I had to direct g++ to the right place. 

Now, if I only use the C code (ignoring C++ for a minute) of the examples in the fann directory and make a QT project within QT creator, it still does not work.

I think I need to link the correct libraries to tell QT Creator how to compile the code, but my attempts so far have not worked.

I attach a small QT project and I would really appreciate it if someone could install libfann1-dev and try and get this is work with QT creator and let me know what I'm doing wrong.

The example is based on the reference guide on the fann website and not the more complicated examples in the release examples/.

Regards,

msbealo

---

### Post by msbealo on 2009-12-27
file attached.

---

### Post by msbealo on 2010-01-04
Ok, I've managed to sort this problem.

I uninstalled all Qt and fann related packages before reinstalling them all again. This did not sort the problem. I then uninstalled fann and searched my system for any fann related files and found quite a few.

Originally I installed fann using the source distribution and then I also istalled the libfann-dev ubuntu package. Once I'd removed all of the self installed fann files and reinstalled the libfann-dev package it all stared working.

The other problem that I was having was that I didn't know now to include the fann library in Qt at compile time. This is done by adding "LIBS += -lfann" to the project file. I think that while finding a solution to this original problem that I installed the additional version of fann.

Thanks for your help *ahem*,

msbealo

---

