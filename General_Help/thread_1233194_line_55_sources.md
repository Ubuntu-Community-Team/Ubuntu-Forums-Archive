---
title: "line 55 sources"
date: 2009-08-06
forum: General Help
---

### Post by allen939711 on 2009-08-06
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'For' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

E: Type 'For' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i am also getting: E: Type 'For' is not known on line 49 in source list /etc/apt/sources.list
E: Unable to lock the list directory



can some one help me with this i can get into my package manager i tried install a z600 printer and got this 

i need to know step by step what to do !!!!!

ubuntu 9.4

---

### Post by drs305 on 2009-08-06
You have errors in your sources.list. You can open it for editing with:
```

gksudo gedit +49 /etc/apt/sources.list

```
If you don't know how to open a terminal: Applications, Accessories, Terminal. When you run the command above, it will ask for your password. Type it but you won't see it - hit ENTER when you've typed it completely.

Also look at line 55 for another error. All sources.list lines should begin with the word "deb" or a # symbol.

If you don't understand what to look for, post your sources.list here and we can look at it.

---

### Post by bostonaholic on 2009-08-06
post your /etc/apt/sources.list file.

---

