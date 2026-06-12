---
title: "&quot;No such file or directory&quot; error on executing binaries"
date: 2010-12-10
forum: General Help
---

### Post by spencercarran on 2010-12-10
I am actually running Linux Mint 10 64-bit, which should be essentially identical to Ubuntu 10.10.

When I attempt to execute a Linux binary file that I have downloaded from the internet, I get the error "No such file or directory." I have eliminated all sources of user error as explanations:
I am in the correct directory; 'ls' displays the file in question as present.
I am prefixing the command with './'
The permissions on the files are correct and they are marked as executable

The specific cases where I have problems are with the Mathematica Player freeware program from Wolfram, the Foldit protein folding game, and the XPP-Aut dynamical system program. I have used the Foldit and XPP-Aut binaries previously on other Linux distros, including Ubuntu, so I don't believe there is any problem with the files themselves.

Does anyone have an idea why Mint can't execute these binaries?

---

### Post by oldos2er on 2010-12-10
If it's a 32-bit executable, you'll need to install ia32-libs to run it.

---

### Post by spencercarran on 2010-12-10
That fixed it. Thank you.

---

### Post by oldos2er on 2010-12-10
You're welcome.

---

