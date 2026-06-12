---
title: "Set the source of apt-get to a directory instead of archive.ubuntu.com"
date: 2011-08-31
forum: General Help
---

### Post by Raam General on 2011-08-31
Hello!
I'm italian and I can't speak/write English very well, therefore sorry for errors or sentences not very easy to read (in ForumUbuntu-it nobody wouldn't answer me).
I had to reinstall Ubuntu 10.04 because of a problem and now I must install many programs.
Whenever I install a program I rescue the deb packages from /var/cache/apt/archives so I can re-use them if (for some reason) I must reinstall the program (like now).

Previously I put deb packages of a single program in /var/cache/apt/archives and the dependencies were already satisfied by other programs installed, but now no software is installed so I must consider the whole directory of my packages that I CAN'T put them in /var/cache/apt/archives because they are about 1GB.

I know that apt-get/synaptic/ubuntu-software-center download from [archive.ubuntu.com]("http://ubuntuforums.org/showthread.php?t=1836468");
can I set the source of apt-get to the directory which contains deb packages instead of [archive.ubuntu.com]("http://ubuntuforums.org/showthread.php?t=1836468")?


I hope you can help me.

---

### Post by dino99 on 2011-08-31
all the deb packages can be installed with:

sudo dpkg -i *.deb

to do it safely, download or move the deb package(s) into an empty folder, then cd /to/that/folder/ and run the command above.

---

### Post by Raam General on 2011-08-31
I have created a Local Repository, but I'm not able to use it.
After I do the repository, how can I use it?

---

