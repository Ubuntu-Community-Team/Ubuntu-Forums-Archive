---
title: "Azurueus Install?"
date: 2006-05-24
forum: General Help
---

### Post by veev on 2006-05-24
I installed Java and added multiverse to my repository. Then I typed:

sudo apt-get install azureus

BUT I got an error?
Reading package lists... Done
Building dependency tree... Done
Package azureus is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package azureus has no installation candidate

Any ideas?

Also, how do you do that thing on this forum so that it draws  a rectangle and uses a different font when you want to show output from your ubunto terminal?

---

### Post by seppe on 2006-05-24
Azureus isn't packaged for Ubuntu. 

A very simple install can be performed by downloading latest version from [Azureus download page on Sourceforge]("http://azureus.sourceforge.net/download.php"), unpacking it on a folder in your home directory (es. [FONT="monospace"]~/programs/azureus/[/FONT]) and executing the just extracted script [FONT="monospace"]azureus[/FONT].

If you want to let azureus be executable by all users, follow the [HOWTO: Install Azureus (newest, non-repo way)]("http://ubuntuforums.org/showthread.php?t=144546") (written for the benefit of readers of this forum).

---

