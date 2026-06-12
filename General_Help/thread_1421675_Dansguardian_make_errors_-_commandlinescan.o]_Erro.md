---
title: "Dansguardian make errors - commandlinescan.o] Error 1"
date: 2010-03-04
forum: General Help
---

### Post by wolfsden3 on 2010-03-04
I've tried two version of Dansguardian, 2.10 and 2.10.1.1 and I get the same error.  I can't figure out how to fix it.  Any help would be appreciated.

**./configure** seems to run well, here's the 2 commands I tried when I was tinkering:

# **./configure --enable-clamd=yes --enable-commandline=yes --enable-fancydm=yes --enable-trickledm=yes --enable-ntlm=yes --enable-email=yes**

# **./configure --enable-clamd=yes --enable-commandline=yes --enable-fancydm=yes --enable-trickledm=yes --enable-ntlm=yes --enable-email=yes --enable-pcre**

I then type the command:  **make**

This is when I get this error on both versions:

deps/dansguardian-commandlinescan.Tpo -c -o dansguardian-commandlinescan.o `test -f 'contentscanners/commandlinescan.cpp' || echo './'`contentscanners/commandlinescan.cpp
contentscanners/commandlinescan.cpp: In member function ‘virtual int commandlineinstance::scanFile(HTTPHeader*, HTTPHeader*, const char*, int, const char*, const char*)’:
contentscanners/**commandlinescan.cpp:293: error: ‘fdopen’ was not declared in this scope**
contentscanners/**commandlinescan.cpp:294: error: ‘fgets’ was not declared in this scope**
contentscanners/**commandlinescan.cpp:300: error: ‘fclose’ was not declared in this scope**
contentscanners/**commandlinescan.cpp:302: error: ‘fgets’ was not declared in this scope**
make[2]: *** [dansguardian-commandlinescan.o] Error 1
make[2]: Leaving directory `/tmp/dansguardian-2.10.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/dansguardian-2.10.1.1'
make: *** [all] Error 2

I can't find anything on the net about it other than other distro bugzilla reports which is why I tried the latest stable release just to see what would happen.  I did poke around in /src/contentscanners and looked at the commanlinescan.cpp but I don't know C programming so I'm not sure what to do there :-)

Any help would be greatly appreciated!  I wanted to use 2.10 so I could also use webmin to manage it.

Thanks in advance!

---

### Post by rnerwein on 2010-03-04
hi
there is the is an include of the header file "stdio.h" missing. the functions which are not declared are
defined there ( functions for charachters, strings, streams ... etc. )
in c-code:
#include <stdio.h>
ciao

---

### Post by wolfsden3 on 2010-03-04
YOU ARE THE MAN / woMAN!

I also had to add this to "fancy.cpp" in the src/downloadmanagers directory.

#include <stdio.h>

Once I added that to the cpp files I didn't get the errors!  I have been BANGING my head on this for days!  WHOOPIE!

Thanks so much for the post.

---

