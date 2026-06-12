---
title: "How do I recompile an installed package?"
date: 2006-02-09
forum: General Help
---

### Post by remery on 2006-02-09
Sorry for what is undoubtedly an easy question, but I'm pretty new to Debian-based distros.

At work, we've decided to run Ubuntu for our web server. We need PHP 5 with MSSQL support (I've been told that the sybase library won't give us everything or work the same). I am capable of downloading the PHP source code and compiling it, but management wants package management with upgrade support (and that would be easier on our administrators anyway).

Ideally, I want to be able to use synaptic/apt to install PHP 5 and the freetds libraries, and then re-compile PHP with mssql (understanding that each upgrade to PHP would require a re-compile).

Is there a fairly easy way to accomplish this, and if so, how?

Thanks in advance,
Rick

---

### Post by taurus on 2006-02-09
If you want to build something from source, you need gcc and all the essential things, so before you dive into it, better run this command first,

sudo apt-get install build-essential

Now, download the source and unpack it.  Then, change to the new directory and you probably have to do something like

./configure
make
make install 
--or replace the "make install" with 
make checkinstall
(so you can use synpatic or apt-get to upgrade it later!)

And of course, always read the README/INSTALL first before you build something...

---

### Post by RAOF on 2006-02-09
You can use "apt-get source <packagename>" to get the source & debian control stuff for an Ubuntu package.  Then you can edit the debian/rules file - that contains the ./configure options used to build the package.  Add/remove whatever you want there, then use dpkg-buildpackage to rebuild the package and you can install it.

Voila - an ubuntu package with support for what you want compiled in!

---

### Post by remery on 2006-02-09
[QUOTE=RAOF]You can use "apt-get source <packagename>" to get the source & debian control stuff for an Ubuntu package.  Then you can edit the debian/rules file - that contains the ./configure options used to build the package.  Add/remove whatever you want there, then use dpkg-buildpackage to rebuild the package and you can install it.

Voila - an ubuntu package with support for what you want compiled in![/QUOTE]

That's **exactly** the information I was looking for.

Thanks!
Rick

---

### Post by remery on 2006-02-10
I've had moderate success with this, but ran into a problem (this may be more technical than a user-space problem, so if there's a better forum for this please let me know).

I installed most of the requested dependencies and ran dpkg-buildpackage. After about 45 minutes of compiling/installing messages, I get the errors shown in the screenshot (by the way, I can't imagine why it would matter, but I'm doing all of this in a VMWare virtual machine). I've checked the path specified in the messages and, while the directory exists, it is empty; there are no .so files (which may be why I'm getting the error?).

Thanks in advance for any help,
Rick

---

