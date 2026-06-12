---
title: "azureus can't find java"
date: 2006-04-19
forum: General Help
---

### Post by bluecalx on 2006-04-19
i recently installed azureus on breezy as per the instructions on a very lovely forum post - alas, it worked fine yesterday but now....

> Starting Azureus...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE [java = #]
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)


sun java re is up and raring to go... tried making a few soft folder links with no joy.... help please!

---

### Post by njzillest on 2006-04-19
use automatix, its in one of the threads. It will install all the java settings you need, and it installs Azureus.




-----------
everything is automatic, no research needed

---

### Post by darknightuk on 2006-04-19
dumb question i know but you have installed java i take it?

---

### Post by bluecalx on 2006-04-19
yes... absolutely... and using automatix doesn't seem to help either

---

### Post by darknightuk on 2006-04-19
try java -version in console, what do you get?

---

### Post by bluecalx on 2006-04-19
here: > # An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb787feb1, pid=12756, tid=3084494528
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# V  [libjvm.so+0x247eb1]
#
# An error report file with more information is saved as hs_err_pid12756.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted


uninstalling/reinstalling javasun now... hope it works

---

