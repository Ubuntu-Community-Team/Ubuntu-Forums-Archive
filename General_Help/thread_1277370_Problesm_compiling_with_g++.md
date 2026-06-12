---
title: "Problesm compiling with g++"
date: 2009-09-28
forum: General Help
---

### Post by PaulAJohnston on 2009-09-28
Hi
Using 9.04 with gcc version 4..3.3 to compile some fairly old code (giza++ for those interested) I know about the deprecation of c++ header files but it complains about stream.h being missing. As this is not in the source I looked in /usr/include and no stream.h
Yes to strings.h, stdio.h signal.h etc but no stream.h
[http://ubuntuforums.org/showthread.php?p=7502764](http://ubuntuforums.org/showthread.php?p=7502764) starts this thread but ends at the interesting bit quote "Dear gsocker, should I change <stream.h> to <iostream> also?
Because there is no file name stream, I tried this."

Anyone able to help me?
Regards Paul

---

### Post by Giblet5 on 2009-09-28
It depends on what/where the old code expected <stream.h> to be.

Comment it out, compile, and see what comes up undefined.

AFAIK, I/O streams have always used iostream.h, and stream.h is Ancient UNIX (pre-jurassic) for stream devices. But it could be a header included with the code just as easily...

It sounds like you need a programmer.

---

### Post by PaulAJohnston on 2009-09-28
Very jurrasic indeed :-)

"was  developed by the Statistical Machine Translation team during  the summer workshop in 1999 at the Center for Language and Speech  Processing at Johns-Hopkins University"

Just going to build another VBox and see how it goes with 8.04 then maybe able to port the binaries to my 9 machine.
Thanks Paul

---

