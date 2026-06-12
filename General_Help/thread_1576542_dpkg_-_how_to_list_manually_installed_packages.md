---
title: "dpkg - how to list manually installed packages?"
date: 2010-09-17
forum: General Help
---

### Post by jafa81 on 2010-09-17
Hi,
I'd like to list all packages I installed since the installation. 
The tricky part is that I don't care for dependencies - only clean list of what I ordered to install. I went through man pages and I did not find anything relevant. 

Also /var/log/apt/history* doesn't say what I requested and what came as a dependency. 

For gentoo-aware folks, I am looking for something like "world" file. 

Thank you,
Mike

---

### Post by ajgreeny on 2010-09-17
I am not aware of any way to do what you want, as there is no obvious way to discriminate between the packages that you asked to install and those added by the system as dependencies.

A full list of everything on the machine can be made easily with ```
sudo dpkg --get-selections > installed-software
```which will produce a txt file called installed-software in your home, but that may not be any help to you, I'm afraid.

---

