---
title: "Such a thing as a C++ GUI compiler for ubuntu?"
date: 2009-09-23
forum: General Help
---

### Post by gksudo on 2009-09-23
Hello, I was wondering if there was such a thing as a C++ gui compiler for ubuntu. Thanks

---

### Post by dpb on 2009-09-23
What you are most likely looking for is an IDE (Integrated Development Environment).  There are a number of IDEs for Ubuntu, and there is great debate over which one is better, etc.

Just search "IDE Ubuntu" on google to get an idea.

Here are a couple links to get you started:

  Eclipse CDT: [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)
  KDevelop: [http://www.kdevelop.org/](http://www.kdevelop.org/)

Note that there is no such thing as a C++ GUI Compiler.  g++ (GCCs C++ Compiler) is the standard C++ compiler for linux.  It's a command line tool and is used to compile both command line and GUI Applications.

Hopefully that answers your question, but if not, you may want to clear up your question a bit more.

Good Luck!

---

### Post by gksudo on 2009-09-23
Thanks!

---

### Post by morgan_greywolf on 2009-09-23
> **dpb said:**
> Note that there is no such thing as a C++ GUI Compiler.  g++ (GCCs C++ Compiler) is the standard C++ compiler for linux.  It's a command line tool and is used to compile both command line and GUI Applications.
Good Luck!

This is also true of so-called "GUI compilers" like Visual C++ -- what you have is IDE that calls some command-line compiler.

Aside from Eclipse CDT and Kdevelop, there's also Anjuta, which you can install either from Synaptic or with 'sudo apt-get install anjuta' in a terminal window.

Of course, Real Programmers(tm) use Emacs. :P

---

