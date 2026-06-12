---
title: "Installing QDevelop?"
date: 2011-03-19
forum: General Help
---

### Post by khoraski on 2011-03-19
I've been trying to find out how to code or create desktop apps in Linux Ubuntu for a little while now. 

I found [this](http://www.clivecooper.co.uk/tutorial/index.html) tutorial. Which I'm trying. But QDevelop is down and I can't found out how to install it.

Any other tutorials or help you can give me?

---

### Post by tgalati4 on 2011-03-19
You could try quickly:

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

QDevelop looks old and perhaps is not supported anymore since the website is parked.  However I was able to download the tarball.  Just follow the instructions, although they may need to be modified since they were written for Edgy Eft.

apt-cache search qt4
sudo apt-get install libqt4-core libqt4-debug libqt4-gui libqt4-qt3support libqt4-sql qt4-designer qt4-dev-tools qt4-doc qt4-qtconfig

Some of those package names may have changed so keep a list of what doesn't install.

---

