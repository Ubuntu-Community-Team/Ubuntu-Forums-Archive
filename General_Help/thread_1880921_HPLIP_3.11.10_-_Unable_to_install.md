---
title: "HPLIP 3.11.10 - Unable to install"
date: 2011-11-14
forum: General Help
---

### Post by hiyono on 2011-11-14
After upgrading to 11.10, I noticed my printer started ignoring the top margin. Figuring I'd just try and update hplip to 3.11.10, I've now been having problems installing it. 

Running the automated script results in a make error with status code 2 when attempting to sudo make install.

Running sudo make install manually returns the following:

```
make: stat: GNUmakefile: Permission denied
make: stat: makefile: Permission denied
make: stat: install: Permission denied
make: *** No rule to make target `install'.  Stop.
```

Any clues?

---

### Post by ballantony on 2011-11-14
I'm not sure about the answer to this problem, but I seem to remember having to remove hplip 3.10.7 completely before I could get 3.10.11 to install.  I used synaptic to search for all the bits.  If no one comes up with a better solution, you could try that!

---

### Post by hiyono on 2011-11-14
Hmm, well I did apt-get purge & autoremove first. I don't know if that counts?

---

### Post by ballantony on 2011-11-14
I think I did the same, but it didn't work.  I seem to remember there were bits left behind.

---

### Post by hiyono on 2011-11-14
Hrm. I guess my (secondary) issue now is that I can't authenticate to access the Software Center or Synaptic. 
I work in a lab, and my account is accessed through a virtual server. I have sudo access, but on the machines themselves, our admin is the only actual user. 
There's no option allowing me to authenticate under my own account when I try to install / remove through the Software Center or Synaptic.

---

