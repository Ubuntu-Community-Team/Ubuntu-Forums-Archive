---
title: "a few questions of how to"
date: 2010-12-21
forum: General Help
---

### Post by dblanchard1278 on 2010-12-21
Hello all

I'm new to using Ubuntu 10.10 64, in fact I'm a new linux user and I have some questions on how to do some stuff on it since I'm an avid windows user.

My first question is, what things do I need to compile and install programs? I tryed it with open ssl but got errors because stuff was missing and I wanted to know what I needed to make sure I don't run in to problems again.

My second is, how do I find the installed packages I downloaded and installed? I installed a package and I want to use it and I can't find it anywhere to run it? 

any help is greatly appriciated
thanks

---

### Post by 3rdalbum on 2010-12-22
1. You need the "build-essential" package to start off with, plus the development libraries appropriate for the program you are compiling. If you get an error message about something being missing, try looking in Synaptic Package Manager and downloading any relevant packages with names that end in "-dev".

OpenSSL is very much in the repositories, and should be installed when you install some repository software that requires it.

Compiling software is not really something a new Linux user is expected to do... are you sure the software you're trying to compile is not already available from a PPA or other repository?

2. Usually, graphical programs will appear in your menu. If you install them using Ubuntu Software Center, it will tell you where to find them. If they don't appear in the menu, they might not be graphical programs - for instance, they might be panel applets, command-line utilities, libraries, or documentation. You can find where they have installed by selecting the package in Synaptic Package Manager, right-clicking and choosing Properties, and then going to the "Installed Files" tab.

---

