---
title: "I did a dummy"
date: 2011-11-10
forum: General Help
---

### Post by jredburn on 2011-11-10
I am unhappy with the way Ubuntu 11-10 runs (sometimes) on my old Dell tower.  So I was doing a TAR on my home directory and pipping it to an external drive.  It did not go there, it went to my root directory.  Now i do not have enough space on the hard drive for the program to run.  It will not load in normal configuration.
I can get it to load in safe mode and run it from a terminal page.
My problem is that I cannot remove  the  .tar file from the root directory because it is a "read only " file. I have tried to change the permissions but it does not work.  It tells me it is changing permissions but it does not do it.
I have gone into my home dir. and removed a lot of files that I don't really have to have and that did not free up enough memory to get a boot into the GUI
I need some advice on how to get that .tar file out of my root dir.
Any words of wisdom will be appreciated
Regards
Joe

---

### Post by HermanAB on 2011-11-10
This should work:
sudo rm -f /filename

---

