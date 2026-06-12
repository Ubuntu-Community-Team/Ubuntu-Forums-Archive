---
title: "please help"
date: 2009-08-06
forum: General Help
---

### Post by sbomb on 2009-08-06
In following the install guide below, i receive an error message. can you guys please tell me if you see anything wrong in the guide and/or my konsole paste. Thanks in advance.

2.
Enter terminal mode and change to root account by this command.
( sudo –s )
Rebuild the TouchKit driver.
3.1) Locate the extracted directory. And go to the subdirectory
/touchkit/include then type [COLOR=Navy]make new[/COLOR]
3.2) change the directory to /touchkit then type [COLOR=Navy]make all[/COLOR]
The touchKit driver will be rebuild. ( Some packages must be
installed and well configured ).
3.3) type make install to begin to install at the same directory /touchkit
3.

it results in the following:

root@dce:~/touchkit/include# make new
rm -f configSTR.h configSTR.mak configINT.h configINT.mak touch.tcl
tclsh ../utility/tcl2h.tcl configSTR.tcl > configSTR.h
/bin/sh: tclsh: command not found
make: *** [configSTR.h] Error 127
root@dce:~/touchkit/include#

---

### Post by sbomb on 2009-08-06
can anybody help?

---

### Post by howefield on 2009-08-06
Your machine can't find the command "tclsh" therefore cannot complete the instruction.

---

### Post by sbomb on 2009-08-06
thanks.....how can i solve the issue?

---

### Post by warp99 on 2009-08-06
Enable the universe repositories in Synaptic and install the "tclx8.3" package. Here are the detailed on the package:

[http://packages.ubuntu.com/jaunty/tclx8.3](http://packages.ubuntu.com/jaunty/tclx8.3)

Edit:
You probable need tkx8.3-dev so install that also.

---

### Post by sbomb on 2009-08-06
thanks for the reply, i'll try that and get back to u with results, thanks again, really appreciate it.

---

### Post by warp99 on 2009-08-06
Just to let you know that you may need tclx8.4-dev and tkx8.4-dev instead depending on the requirements of the build. 

Edit:
Also my earlier post stated you need tclx8.3, but you also need tclx8.3-dev. I think you probable knew what I was talking about anyway

---

