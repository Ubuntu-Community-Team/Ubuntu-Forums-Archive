---
title: "vb,net library in mono-dev"
date: 2011-05-24
forum: General Help
---

### Post by ian.th on 2011-05-24
got an ubuntu server 11.04 working with mono-dev installed and vbnc so I am trying an vb.net application that requires an external library. That library (phidgets 2.1) is installed but the application when I try and compile it in mono I get an error that is saying it cannot find the library for phidgets
so I need to know how to link the phidget library
 
I have tried
import phidget.io

---

### Post by searchfgold6789 on 2011-05-24
It could be development headers you are missing. Try installing something like 'phidget-dev'.

---

### Post by ian.th on 2011-05-24
ok will try
 
how do I tell my vb.net application to link it

---

### Post by ian.th on 2011-05-24
ok if my application has 
 
import Phidgets.IO
 
it seems to compile but when I run it I just get a blank window not my form
 
do I need Gkt
 
can you help me if you see all of my vb.net code via a pm

---

### Post by ian.th on 2011-05-26
hmm seems mono need phidgets21-windevel but how do I install that in linux

---

