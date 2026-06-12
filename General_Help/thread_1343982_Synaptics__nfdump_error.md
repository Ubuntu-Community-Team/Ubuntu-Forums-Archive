---
title: "Synaptics : nfdump error"
date: 2009-12-02
forum: General Help
---

### Post by almufadado on 2009-12-02
I am running Ubuntu 9.10 Karmic Koala x64

For testing purposes, I installed wanguardian, a non-free application, composed of 3 debian apps.
I first got stuck when the installation with graphic dpkg because it did not detect some dependencies.
After that I installed the 3 apps in the terminal, following exactly the provided instructions, and was successful in the installation process with no error messages. 

But since then Synaptics returns this message , even if the other dialog states it installed successfully the choosen application
The message is as follows:

> 
E: nfdump: subprocess installed post-installation script returned error exit status 1
In the console this is what it reads:

> Selecting previously deselected package unrar.
(Reading database ... 167559 files and directories currently installed.)
Unpacking unrar (from .../unrar_1%3a3.9.3-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nfdump (1.5.7+20081221-3) ...
invoke-rc.d: initscript nfdump, action "start" failed.
dpkg: error processing nfdump (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up unrar (1:3.9.3-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.

Errors were encountered while processing:
 nfdump
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
 .Then, to report this, I tried openning, as user, the "report a problem..." and it fails to start.

How can I repair this ?
Thanks in advance

---

### Post by almufadado on 2009-12-03
It seems it's a bug since 9.04 to 9.10 and affecting mostly am64 distros.

Going back, I also installed "aptitude", a command line package manager with a graphic terminal-like interface, which could be the cause of the new error.

Also discover how to use the crash report ... just double click on a crash report dump file ... nice !

---

### Post by almufadado on 2009-12-07
nfdump is also a dependecy from other security related packages I installed . 

As all of this where, according to docs, network related I fail to see how it got stuck on synaptics, so could this be a security breach ?

Nfdump also behaves bad in the process of uninstalling itself .

Well I decided to downgrade to 9.10 koala x32.

So let's try to mess this up again  :)

---

