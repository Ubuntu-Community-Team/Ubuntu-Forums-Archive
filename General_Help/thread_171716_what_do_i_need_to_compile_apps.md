---
title: "what do i need to compile apps?"
date: 2006-05-07
forum: General Help
---

### Post by mistamcgoo on 2006-05-07
i've been trying to install some apps from kde-apps like kommando and kxdocker. I download the tarball, unpack it to a subdir in my home folder. I follow the install instructions(./configure), but with both i end up with the same error message
```

configure: error: C++ preprocessor "/lib/cpp" fails sanity check

```
do i need to install other compilers? i have gcc3.3 and cpp 3.3 installed. 
am i doing something wrong?

---

### Post by Sef on 2006-05-07
Did you download build-essential?  If not, then download that.

Konsole

kdesu apt-get install build-essential

---

### Post by mistamcgoo on 2006-05-07
that got me a bit further, thank you 

now both installations give me another error message 
```

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

is there something else i am missing?

---

