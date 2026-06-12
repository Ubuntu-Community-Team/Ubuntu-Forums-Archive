---
title: "Trouble with Cygwin"
date: 2009-12-02
forum: General Help
---

### Post by arianamiri on 2009-12-02
So i'm working on a project for a class i'm taking that uses the SDL-1.2.14 graphics package for cygwin.  I'm having trouble setting up SDL.  ./configure worked properly and i installed make without any errors, but now when type in "sudo make install" i get an error that reads "bash: sudo: command not found."  IS there a package in cygwin that i need to install?  If it makes any difference i'm running the cygwin environment on a windows vista 32 bit machine.

---

### Post by diaa on 2009-12-02
You don't need to compile SDL from source on Cygwin, use the Cygwin installer to install it.
Also I usually prefer to use native stuff so if I were you I'd stick with the Win32 SDL, I've used it and it works pretty well.

---

