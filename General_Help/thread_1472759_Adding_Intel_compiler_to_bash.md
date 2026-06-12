---
title: "Adding Intel compiler to bash"
date: 2010-05-04
forum: General Help
---

### Post by TheDestroyer on 2010-05-04
Hello people,

I'm still a beginner in Linux world, and I would like to learn something more about bash.

I installed recently the Intel Fortran compiler. I know where the executable of the compiler is, but I don't know how to make it as a global command, the path is:

/opt/intel/Compiler/11.1/072/bin/intel64/ifort

I would like to write "ifort" in whatever directory and get the compile to do its job. What I know is that this is done by bash. Could someone please explain how this is done?

Thank you

---

### Post by dcstar on 2010-05-05
> **TheDestroyer said:**
> Hello people,

I'm still a beginner in Linux world, and I would like to learn something more about bash.

I installed recently the Intel Fortran compiler. I know where the executable of the compiler is, but I don't know how to make it as a global command, the path is:

/opt/intel/Compiler/11.1/072/bin/intel64/ifort

I would like to write "ifort" in whatever directory and get the compile to do its job. What I know is that this is done by bash. Could someone please explain how this is done?

Thank you

```
echo $PATH
```

You can change the default PATH in /etc/environment.

---

