---
title: "Maya 2011 and Missing Libssl.so.6"
date: 2010-05-30
forum: General Help
---

### Post by sgreum on 2010-05-30
Hello all,

I have been trying to run Maya 2011 on my install of Kubuntu Lucid. It appears to have installed correctly but when I run it I get the error "**error while loading shared libraries: libssl.so.6: cannot open shared object file: No such file or directory**". I have searched everywhere I can think of for a solution but I cannot find one anywhere.

I tried making the symbolic link to libssl.so.0.9.8 without any errors but when I type the command "maya" in bash I get the above error again.

Please, does anyone have a solution to this problem so that I can get this software running? It's driving me nuts.

---

### Post by ankspo71 on 2010-05-30
Hi,
Have you tried installing "libssl-dev"?
This link might help too.
[http://lime-technology.com/forum/index.php?topic=5668.0](http://lime-technology.com/forum/index.php?topic=5668.0)
Hope that helps.

---

### Post by sgreum on 2010-05-30
Thanks, that worked perfectly.

Now I have to work out how to fix the Maya licensing issue so I can actually put in the serial number.

Thanks for your help.

---

