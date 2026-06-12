---
title: "OpenOffice crash in macros"
date: 2006-02-12
forum: General Help
---

### Post by ivanhelguera on 2006-02-12
Hello, 
I have QUITE a problem with my ubuntu system. 
OOo2 writer crashes every time I go to macros - Run macro - OO macros - Launcher...
it dies right away. 
This happens on both my computers - one a AthlonXP2.8 and a PIII 800 
Am I the only one to have it?
IH

---

### Post by nanotube on 2006-02-12
hmm... dont know, i do not have the same problem... try upgrading openoffice?
(see instructions for that at the bottom of this page:
[http://www.oreillynet.com/sysadmin/blog/2006/02/updating_ubuntu_for_openoffice.html](http://www.oreillynet.com/sysadmin/blog/2006/02/updating_ubuntu_for_openoffice.html)
)

---

### Post by atoponce on 2006-02-12
Nope, you are not the only one.  On both Windows and Linux, I have the exact same problem.  I have the latest OpenOffice.org release, and suspect that it is a Java issue and not a OpenOffice.org issue.  It matters not whether I use Writer or Calc.  Frankly, I am getting more and more frustrated with OpenOffice.org because of the Java implementation.

---

### Post by ivanhelguera on 2006-02-13
> hmm... dont know, i do not have the same problem... try upgrading openoffice?

Nope. I have OOo downoaded by Automatix - About says 2.01 breezy
I had the very same problem on the original breezy versions. 
Can you *confirm* being able to run dicoo[LEFT][/LEFT] (tools->Macro-> Run Macro> OOmacros->Launcher *here it crashes* - Dicoo)?

>  On both Windows and Linux, I have the exact same problem

It may well be, as you suggest, a java problem. I have the thing working on my other Linux install (Vector Linux SOHO 5.1), as well as one of the windows installs (the other does not see any java - dependent macros). It looks as if there is something wrong with the very Ubuntu implementation of OOo2. 

**EDIT**
Oh yes, it is a Java problem. I ran OOo from command line, and here's what I got: 
> #
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb070d377, pid=7181, tid=3061892800
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# C  [libsvx680li.so+0x326377]
#
# An error report file with more information is saved as hs_err_pid7181.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
KCrash: Application 'soffice.bin' crashing...
X IO Error

Best, 
IH

---

