---
title: "Eclipse with C++? How to?"
date: 2010-06-06
forum: General Help
---

### Post by crixtiano on 2010-06-06
Hi, 

I use Eclipse 3.5 from Ubuntu 9.10 repository.

Please, how to use Eclipse to programming with C++ language?

Thank you!

Cristiano M. Magalhaes

---

### Post by giddyup306 on 2010-06-06
> **crixtiano said:**
> Hi, 

I use Eclipse 3.5 from Ubuntu 9.10 repository.

Please, how to use Eclipse to programming with C++ language?

Thank you!

Cristiano M. Magalhaes

When I used Eclipse I was using it in Windows and I think there is a plugin for it.  If not I think there is one for Net Beans.

---

### Post by GregBrannon on 2010-06-06
There's help here:

[http://www.eclipse.org/cdt/]("http://www.eclipse.org/cdt/")

The topic has also been discussed many times in Ubuntu's Programming Talk forum.

---

### Post by pedro_orange on 2010-06-06
As a side note, you don't actually need Eclipse or Netbeans to write code.
You can get a plug-in for gedit to do syntax highlighting (or whatever text editor you like to use) and as long as you have done:

```
sudo apt-get install build-essential
```

You can compile from the command line with something like: 

```
g++ code.cpp -o app.o
```

(You can use flags like wall & pedantic etc) Then to run it simply do something like:

```
./app.o
```

---

### Post by drdos2006 on 2010-06-06
Code::Blocks has a very nice IDE and debugger for writing C++ code.

regards

---

### Post by Leppie on 2010-06-06
this is from the synaptic description for eclipse:
> This package provides the whole Eclipse SDK, along with the Java Development
Tools (JDT) and the Plugin Development Environment (PDE).  [COLOR=Red]Please note that
many plugins will fail to install if you don't have the eclipse-pde package
installed.[/COLOR]

---

