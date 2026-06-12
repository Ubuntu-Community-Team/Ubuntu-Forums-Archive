---
title: "apps. directory..."
date: 2012-02-03
forum: General Help
---

### Post by jjb945025 on 2012-02-03
hello..can anyone enlighten me on the whereabouts of the application directory. i suppose that this directory is like the installation directory in windows OS's.i believe that when a program is installed, the applications directory is where the main folder, named after the installed program, containing all of the dll files, ect., is located (is this correct??) and if so.. where is the applications directory located in ubuntu?- thanx in advance...

---

### Post by carl4926 on 2012-02-03
It's not like windows at all !
But the applications are mostly at /usr/lib/

---

### Post by 3rdalbum on 2012-02-03
> **jjb945025 said:**
> hello..can anyone enlighten me on the whereabouts of the application directory. i suppose that this directory is like the installation directory in windows OS's.i believe that when a program is installed, the applications directory is where the main folder, named after the installed program, containing all of the dll files, ect., is located (is this correct??)

Not many things in Linux are similar to Windows, and this is one thing that differs vastly.

On Linux, files get sorted by what they are, not by what program installed them. For instance, libraries generally go into /usr/lib, icons go into /usr/share/icons, the "manual" goes into /usr/share/man and the actual binary goes into /usr/bin.

This is subject to change - programs you've compiled will go into /usr/local instead of /usr; and there are other oddities.

Sounds like a mess? Well, it's not. Your desktop environment knows exactly where to look for menu entries (/usr/share/applications) and the icons (/usr/share/icons). Other programs that use the same pieces of code know to look in /usr/lib. The manual system knows to look in /usr/share/man. The command-line knows to look for the actual program binaries in /bin, /usr/bin or somewhere similar.

I hope that satisfies your curiosity to a point. Feel free to look around your system. If you'd like to know where the files are for a particular package, you can download Synaptic Package Manager which gives you the ability to look at exactly where every file associated with a package is.

---

### Post by d2btoo on 2012-02-03
@op: Type this in terminal: 
```
man hier
```

---

### Post by jerrrys on 2012-02-03
A list of all installed packages, there dependences, size, version, etc. can be found in synaptic package manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

To install, open a terminal and enter:

sudo apt-get install synaptic

---

### Post by corncob on 2012-02-03
Did you look at /usr/share/applications/ ?

---

