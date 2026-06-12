---
title: "Install CIL-1.3.5"
date: 2009-08-21
forum: General Help
---

### Post by newport_j on 2009-08-21
I am trying to install cil-1.3.5 on Ubuntu 8.04..

I have followed the instructions carefully. Start in the desktop directory after downloading cil-1.3.5.
 
tar xvfz cil-1.3.7.tar.gz. 

They then give the three commands ; 

 cd cil

./configure
make 
make quicktest

Now ./configure works fine - no errors here at all. The next command

make works for awhile and then it crashes with the error message.

File "obj/x86_LINUX/feature_config.ml", line 4, characters 1-3:
Unbound value ne
make: *** [obj/x86_LINUX/feature_config.cmo] Error 2

Then make stops.

I am unsure what this error is about. I also use ocaml-3.09.3 on the system. Any higher version of ocaml and the ./configure command generates many error messages. So I do not think that is the problem. I haveI think the right version of ocaml. 

Strangely, when I run the final command make quicktest it says everything successful This is unusual.. So why this error message unbound value of ne? If the end everything is successful.

Anyhelp appreciated. 

Respectfully,

newport_j

---

