---
title: "Working with C++ and QT..problems getting project to work"
date: 2009-06-30
forum: General Help
---

### Post by Hrusk on 2009-06-30
Hey all.....
I'm hoping this is the right place to post this.
I'm a student just starting C++ and working with a professor on one of his projects. I need to get the project working on my home Ubuntu distro, and I keep having problems with trying to build the project. Heres the relevant lines:

errors I get when attempting to build SeeAsYou project
> 
/home/workstation/SeeAsYou/config/../src/PCA.h:10: error: gsl/gsl_blas.h: No such file or directory
/home/zhoekstra/SeeAsYou/config/../src/PCA.h:11: error: gsl/gsl_linalg.h: No such file or directory 

relevant gsl includes in .pro file
> 
unix {
  DEFINES += UNIX
  LIBS += -L. -L/s/parsons/h/proj/vision/lib/opencv-1.1.0/lib/
  LIBS += -lgsl -lgslcblas -lcv
  INCLUDEPATH += /s/parsons/h/proj/vision/lib/opencv-1.1.0/include
}

Obviously I'm not including the gsl code quite right. did a search in the repositories, and all I could come up with was slang-gsl, which I installed.

It would be a great help if anyone knew what to do.

Thanks,
Zach

---

### Post by t4thfavor on 2009-07-01
the make is looking for a folder called gsl/  in which there should be 2 header files. Put them there, and you will be past this error. Your prof has them as he has probably built this app before.

you only need the header files that are throwing the error, so thats all you should be looking for.

put this in google
+gsl/gsl_blas.h

first hit.

---

