---
title: "Ubuntu Terminal"
date: 2010-01-27
forum: General Help
---

### Post by rsynv5 on 2010-01-27
Hi, I've written two programs, one in Perl and one in Python. However, when running them in the terminal, they automatically exit rather  than printing what they're supposed to. Preferably, they'd stay up til I closed them. Can anyone tell me what's wrong/how to fix?

---

### Post by t4thfavor on 2010-01-27
At the end of the program use whatever syntax the language uses to collect user input. Then the prog will wait until you press enter to exit..

so in a C++ app it would be something like

int throwaway;
cin.get(throwaway,1);

From what I understand about python

applock=e32.Ao_lock()   
applock.wait()

---

