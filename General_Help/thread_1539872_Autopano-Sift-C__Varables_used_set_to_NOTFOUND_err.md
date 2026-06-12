---
title: "Autopano-Sift-C / Varables used set to NOTFOUND error while building"
date: 2010-07-27
forum: General Help
---

### Post by Naggobot on 2010-07-27
OS: Ubuntu Karmic 9.10
While building Autopano-Sift-C-2.5.1.according to instructions from
[http://wiki.panotools.org/Hugin_Compiling_Ubuntu](http://wiki.panotools.org/Hugin_Compiling_Ubuntu)

I receved following error

```

CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
PANO13_INCLUDE_DIR
   used as include directory in directory /home/hp550/src/apsc/apsc.hg
   used as include directory in directory /home/hp550/src/apsc/apsc.hg/APSCpp
   used as include directory in directory /home/hp550/src/apsc/apsc.hg/APSCpp/ANN
PANO13_LIBRARIES
    linked by target "autopano" in directory /home/hp550/src/apsc/apsc.hg
    linked by target "generatekeys" in directory /home/hp550/src/apsc/apsc.hg
    linked by target "autopano-sift-c" in directory /home/hp550/src/apsc/apsc.hg/APSCpp

-- Configuring incomplete, errors occurred!

```

This was solved by installing package 

libpano13-dev

---

