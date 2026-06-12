---
title: "CodeLite math.h problem"
date: 2011-05-26
forum: General Help
---

### Post by kiwihurst on 2011-05-26
I have a problem with the CodeLite c-compiler.  While it may not be a Linux/Ubuntu problem I have not been able to find a suggested solution on the CodeLite site or anywhere else so hope someone will recognize the problem and suggest a solution ...

I am using Ubuntu 10.04 LTS, 64-bit version (forget the @#%% Unity desktop!!) and the latest release of CodeLight.  I have tried re-installing twice to no effect.

When compiling regular C language code (I have an extensive library of legacy code) it will not compile functions that contain variables i.e. sqrt(2) is okay, num=2; sqrt(num) is not.  

I suspect this is a problem in the math.h file or one of the files called by math.h but have not been able to locate it.  Other standard library functions seem to work okay, e.g. abs(x) calls to stdlib.h but none of the math.h calls.

It is interesting that the same code compiles and executes okay on CodeLight running under a Windows 7, 64-bit environment.

Any suggestions appreciated - thanks.

---

