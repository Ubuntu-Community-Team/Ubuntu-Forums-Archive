---
title: "Recommended installer for Ubuntu: rpm, yum, apt,...?"
date: 2010-01-13
forum: General Help
---

### Post by pstein on 2010-01-13
If I want to download and install a new software and I have the choice between different packages which one should I prefer for Ubuntu:
 
*.rpm
*.yum
*.apt
 
What are the differences?
 
Peter

---

### Post by jeremy1138 on 2010-01-13
Packages to be installed on Ubuntu are typically .deb files because it is a Debian based operating system, correct?  .rpm is the red hat package manager which is used for Red Hat Linux and Fedora and others like it.  I'm not sure what the other two are...

edit:

I think .yum might be used by SUSE Linux but I'm not sure.  .apt I'm not sure of at all...

---

### Post by r_s on 2010-01-13
yum is a packet-management tool for rpm compatible systems, it works on Fedora.

---

### Post by mk1w86 on 2010-01-13
What software are you trying to install?

---

### Post by jocko on 2010-01-13
> **pstein said:**
> If I want to download and install a new software and I have the choice between different packages which one should I prefer for Ubuntu:
 
*.rpm
*.yum
*.apt
 
What are the differences?
 
Peter
Are you sure those are ".yum" and ".apt" files?
As far as I know, there is a package manager named yum, but it uses .rpm files. Similarly, apt is a debian (and ubuntu) package manager, which uses .deb files.
So if the files you call ".apt" really are .deb files, then that's the ones you should use.

---

### Post by fancypiper on 2010-01-13
The best way is through adding repositories and apt-get for command line installation or Synaptic or the Software Center for the GUI.

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by mick222 on 2010-01-13
most software is available in synaptic or via software centre.  You shouldn't have to download and install like windows.

---

### Post by DestructionsRightHand on 2010-01-13
fyi yum = centOS and a alternative for Fedora

---

