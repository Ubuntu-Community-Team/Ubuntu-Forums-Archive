---
title: "Changing home config files to links?"
date: 2011-08-18
forum: General Help
---

### Post by DheathNone on 2011-08-18
Basically the idea was to have two different linux
installations share a configuration file and I don't want to mount 
the hole home folder in two different installations.
So, I simply moved moved a home folder configuration file to
a different location and soft linked to it from the home folder.
Now that I did that I noticed that always when the program
was started it overwrote the link with a default
configuration file.

I tried moving a few other configuration files and folders to
a different drive and then tried linking to them to home
folder (mainly .zshrc, .mozilla and .gconf). The .zshrc link 
was overwritten. .gconf folder were simply ignored and some 
default settings were used instead. Only Firefox seems to 
follow the soft link. I also checked that the permissions were 
done right.

I expected that all the programs would have followed the 
links and used the configuration files at the different 
location. Is there any way to have the programs use
configuration files and folders that are not located in the
home folder? 

I would like to have only one file if that is possible. I 
also would like to know why exactly the programs won't 
follow the soft links.

This simply should not be a problem. :???:

---

