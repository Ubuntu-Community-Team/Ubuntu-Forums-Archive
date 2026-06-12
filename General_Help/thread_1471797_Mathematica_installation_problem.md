---
title: "Mathematica installation problem"
date: 2010-05-03
forum: General Help
---

### Post by Legion81 on 2010-05-03
I'm installing Mathematica 6.0 on Ubuntu 10.04 (64bit). I almost got all the way through installation (typing in my license number and password) and then the installation failed:

"Creating password file entry in
/usr/share/Mathematica/Licensing/mathpass.


Installation failed. See /usr/local/Wolfram/Mathematica/6.0/InstallErrors."

Here is what was in the "Install Errors" file:

```
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real32' causes overflow in R_X86_64_PC32 relocation
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real64' causes overflow in R_X86_64_PC32 relocation
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real32' causes overflow in R_X86_64_PC32 relocation
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real64' causes overflow in R_X86_64_PC32 relocation
```

I checked in the Mathematica directory and there is not a "Licensing" folder (checked hidden files as well). I'm not sure if that is part of the problem. I have no idea what this error means... any help would be greatly appreciated!

[Edit: I was looking in the wrong directory, the licensing info in "licensing/mathpass" is all there and correct]

---

### Post by phyzjqk on 2010-05-05
It looks a font problem. make sure your language in the current linux session is same as the language version of mathematica.

---

