---
title: "Exit Full Screen Bash in VIrtual Machine"
date: 2010-08-28
forum: General Help
---

### Post by mwmsje on 2010-08-28
I'm running Ubuntu with Sun Virtual Macine on my Mac OSX and I have two problems.

Somhow I have managed to get the Ubuntu screen to go completely black with a bash command line in the centre of it and the characters: "tty6" at the top of it. How do I exit this???

Also I have a file on this virtual machine. Does anyone know how i would put this on my mac without the use of a Pen drive?

---

### Post by Smart Viking on 2010-08-28
> **mwmsje said:**
> 
Somhow I have managed to get the Ubuntu screen to go completely black with a bash command line in the centre of it and the characters: "tty6" at the top of it. How do I exit this???

That is basically a terminal session and X is probably still running, the keyboard shortcut to change between those sessions are alt+F? where ?=1-8, and if you are inside the DE session you must use ctrl+alt+F?, so basically, what you must have done to end up where you are is, you must have somehow typed "ctrl+alt+F6". To get back to the DE, you must enter alt+F7(i think it was F7 might be F8 dont remember), how to do that depends on the OS and programme, in linux you wouldn't be able to do it since you would change session in the OS, and not the virtuel OS, however with mac and sun VM it might be as easy as to just type alt+F7/8, i have no idea.

---

