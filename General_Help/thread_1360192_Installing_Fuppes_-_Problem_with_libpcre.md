---
title: "Installing Fuppes - Problem with libpcre?"
date: 2009-12-20
forum: General Help
---

### Post by PaulStat on 2009-12-20
Hi Guys,  When installing fuppes, I get as far as running ./configure and at the end it tells me:    

checking for PCRE... configure: error: Package requirements (libpcre >= 5.0) were not met:

 No package 'libpcre' found

 Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.  Alternatively, you may set the environment variables PCRE_CFLAGS and PCRE_LIBS to avoid the need to call pkg-config. See the pkg-config man page for more details.

 Any ideas what that means? I checked Synaptic package manager and it seems to think I have libpcre3 version 7.8-3 installed.

 Thanks, Paul

---

### Post by hugmenot on 2009-12-20
You need -dev  packages to install by compilation. They contain the headers needed to build against a library. The  library package itself only contains the binary library itself.

So, install libpcre3-dev also.

---

### Post by vaiocomputer on 2009-12-20
Although I've never tried Fuppes, I'd say that if you're having problems, try PS3 Media Server instead.  There's a guide on the forums or etc. on their google code site, and the software itself has lots of features.

---

### Post by Shhnap on 2009-12-21
vaiocomputer: wow, you simply offered no solutions to anyones problems.

As for the error, that is usually seen when you don't have pkg-config installed which does not seem to be the issue in your case.

As was previously suggested, please install all of the dev packages and required dependancies first before configuring fuppes. You can find them all on the fuppes wiki: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux)

---

