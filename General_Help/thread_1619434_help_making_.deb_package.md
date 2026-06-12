---
title: "help making .deb package"
date: 2010-11-11
forum: General Help
---

### Post by d3v1150m471c on 2010-11-11
I successfully created a .deb package for one of my ongoing projects. However, I need the .deb to install some files and folders in the user's home directory. How do I go about that?

---

### Post by Isaac356 on 2010-11-11
I'm pretty sure it's impossible, seeing that when the .deb is installed, it's installed as root. On a single user system, there's only one user that could have installed it, but on a multi-user system, there's no way to tell who installed it, and therefore which home folder to place those files in.

Generally, things like config files for programs are generated in their respective users' home folders the first time that the program is run. Your best bet is probably to do something like this (i.e. copy the file to the user's folder on startup, if it doesn't already exist)

---

### Post by d3v1150m471c on 2010-11-12
From what I've been researching that seems to be the case. I altered the .deb version to create the appropriate files/folders at runtime which works alright for now. Thanks for the reply.

---

