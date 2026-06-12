---
title: "Configure works but &quot;make&quot; presents the following problem"
date: 2012-07-14
forum: General Help
---

### Post by Gusss on 2012-07-14
/./gui/qopenglplotter.h:193:5: error: ‘GLUquadricObj’ does not

            name a type
            posixpathtools.h: In function ‘bool
            posixpathtools::getcwd(std::string&)’:
            posixpathtools.h:141:27: warning: ignoring return value of ‘int
            fchdir(int)’, declared with attribute warn_unused_result
            [-Wunused-result]
            make[2]: *** [ssr-controller.o] Error 1
            make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
            make[1]: *** [all] Error 2
            make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
            make: *** [all-recursive] Error 1
            dew@ubuntu:~/Desktop/ssr-0.3.3$

Any advice ?

---

### Post by Gusss on 2012-07-14
Noone ?

---

### Post by Gusss on 2012-07-14
For more background :


[http://ubuntuforums.org/showthread.php?t=2024198](http://ubuntuforums.org/showthread.php?t=2024198)

all the details are there.

The following dependancies were installed :

JACK Audio Connection Kit [4]
- FFTW3 compiled for single precision (fftw3f) version 3.0 or higher [5]
- libsndfile [6]
- Ecasound [7]
- Trolltech’s Qt 4.2.2 or higher with OpenGL (QtCore, QtGui and QtOpenGL) [8]
- libxml2 [9]
- Boost.Asio [10], included since Boost version 1.35.

[4] Paul Davis et al. JACK Audio Connection Kit. [http://jackaudio.org](http://jackaudio.org).
[5] Matteo Frigo and Steven G. Johnson. FFTW3. [http://www.fftw.org](http://www.fftw.org).
[6] Erik de Castro Lopo. libsndfile. [http://www.mega-nerd.com/libsndfile](http://www.mega-nerd.com/libsndfile).
[7] Kai Vehmanen. Ecasound. [http://eca.cx/ecasound](http://eca.cx/ecasound).
[8] Trolltech. Qt4. [http://doc.trolltech.com/4.2](http://doc.trolltech.com/4.2).
[9] Daniel Veillard. Libxml2. [http://xmlsoft.org](http://xmlsoft.org).
[10] Boost C++ Libraries. [http://www.boost.org](http://www.boost.org).

---

### Post by steeldriver on 2012-07-14
> **Gusss said:**
> 
- Trolltech’s Qt 4.2.2 or higher with **OpenGL (QtCore, QtGui and QtOpenGL)** [8]


are you sure you got all the prerequisite dev packages? GLUquadricObj seems to be part of the OpenGL Utility Library (GLU)

---

### Post by Gusss on 2012-07-14
> **steeldriver said:**
> are you sure you got all the prerequisite dev packages? GLUquadricObj seems to be part of the OpenGL Utility Library (GLU)

I have gone over them again and again . I think this in the configur emight hold the key :

> configure: WARNING: Found Qt >= 4.7, forcing --enable-floating-control-panel!
checking Searching for non-default Boost include directory... none found.

---

