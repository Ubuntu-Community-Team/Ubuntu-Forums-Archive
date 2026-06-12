---
title: "LaTeX is being annoying and weird"
date: 2010-01-15
forum: General Help
---

### Post by gadget3000 on 2010-01-15
Hi everyone.
Firstly, I am new to LaTeX.
Secondly, my problem is that I am getting errors when the document is compiling normally anyway. I'm trying to use the /text command but says '! Undefined control sequence' and compiles correctly anyway.
I have tried the texlive-full packages from the repos and I've tried from source. I have used the default and installed the amsmath package and it still gives me errors.
Any suggestions?

P.S I am using it like this:
```
$$2^{\text{nd}}$$
```

---

### Post by gadget3000 on 2010-01-15
Nvm.
I didn't know you needed to define he package in the preamble using:
```
\usepackage{amsmath}
```
:D

---

