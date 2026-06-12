---
title: "BASH Alias Rewrite .bin shorthand"
date: 2011-01-13
forum: General Help
---

### Post by micha8l on 2011-01-13
Is there a script I could sticking in my ~.bashrc file that would allow me to invoke .bin files from the BASH without having to type type the .bin part.

For example, I have a file php.bin to invoke this file I'd have to type ./php.bin, but I'd like to just type php. Also would this be a good idea, or am I missing something?

---

### Post by Dr Small on 2011-01-13
If you store your executables in ~/.bin, then add this to your ~/.bashrc:
```
export PATH=.bin/:$PATH
```

---

### Post by WorMzy on 2011-01-13
No, but you can press tab to autocomplete a filename, if that helps.

---

### Post by efflandt on 2011-01-13
I misread and thought you were asking about where to put scripts so they would be in you path (~/bin)

---

### Post by micha8l on 2011-01-13
@wormzy Thanks for reply, I did know this, but I usually use this to complete long names so it didn't occur to me to use it for .bin

@effiandt The file I'm trying to load in shell is /usr/local/zend/bin/zendctl.sh - I don't know where I got .bin from. This is all new to me, so I rephrase.

---

