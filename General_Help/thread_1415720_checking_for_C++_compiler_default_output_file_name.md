---
title: "checking for C++ compiler default output file name..."
date: 2010-02-25
forum: General Help
---

### Post by eawedat on 2010-02-25
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

solution?[IMG]http://nixcraft.com/images/smilies/icon_smile.gif[/IMG]

thanks

---

### Post by giammy on 2010-02-25
> **eawedat said:**
> checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

solution?[IMG]http://nixcraft.com/images/smilies/icon_smile.gif[/IMG]

thanks

Do you have g++ installed?

if you issue the following command:

```

$ g++

```

which is the output?

bye
giammy

---

### Post by eawedat on 2010-02-25
hey giammy
 
[B]The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Ask your administrator to install one of them
g++: command not found[/B]

---

### Post by giammy on 2010-02-25
> **eawedat said:**
> hey giammy
 
[B]The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Ask your administrator to install one of them
g++: command not found[/B]


good: you have to install g++
(apt-get install g++)

bye
giammy

---

### Post by eawedat on 2010-02-25
hey giammy it worked:)
thank you very much :)

---

