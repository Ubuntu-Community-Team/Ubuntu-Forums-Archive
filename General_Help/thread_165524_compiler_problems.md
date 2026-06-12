---
title: "compiler problems"
date: 2006-04-24
forum: General Help
---

### Post by ivansv on 2006-04-24
trying to install some pkgs. keep getting "compiler can't create executables"
thought i was covered there with gcc,gawk.make, etc.
can anybody give a clue as to what's missing? if so 'preciate it, thanks.
much easier using apt, but some of its pkgs are woefully outdated.

---

### Post by spearfish on 2006-04-24
Yeah, I'm having the same problem.  My package manager says that I have gcc-3.4 and gcc-3.4-base installed, however, I can't compile anything.  This is a really frustrating aspect of Ubuntu.

---

### Post by Sef on 2006-04-24
To compile, you need to download build-essential.  

sudo apt-get update

sudo apt-get install build-essential

---

### Post by ivansv on 2006-04-24
thanks sef, will try it.

---

### Post by elettronicha on 2006-04-25
If, even after having installed "build-essential", you get error messages, better you post here the output of the ./configure command.

---

### Post by Packman5280 on 2006-04-25
I have installed build-essential, and I still get the same error message.  not sure what you mean by "./configure".  explain more?

---

### Post by tsrjzq on 2006-04-26
[QUOTE=Packman5280]I have installed build-essential, and I still get the same error message.  not sure what you mean by "./configure".  explain more?[/QUOTE]
./configure is to configure something for compiler, for example, the compiler options,  
the location to install the package or software, the libraries to link....
generally, to install software from source code, ./configure && make && make install are necessary.

---

