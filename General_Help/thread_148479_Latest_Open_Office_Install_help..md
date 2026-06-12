---
title: "Latest Open Office Install help."
date: 2006-03-22
forum: General Help
---

### Post by matthewinuk on 2006-03-22
I downloaded the installation for linux from open office's website. The file is named OOo_2.0.2_LinuxIntel_install_wJRE.tar.gz but i dont know how to install it. After extraction I cant find an install script. Help please. Also, i downloaded the version with JRE? Do i need this?

---

### Post by chuckyp on 2006-03-22
Why not just install with apt-get or synaptic?

---

### Post by matthewinuk on 2006-03-22
because apt-get doesnt have this version. I need the latest version so my ppt presentations dont crash the openoffice

---

### Post by hagen00 on 2006-03-22
You don't want to use synaptic for OOo i think. The latest version is the way forward. Anyway...this should work. 

1. Put the .tar.gz folder into /opt
2. untar it:  tar –xvzf OOo_filename.tar.gz
3. type /opt/openoffice.org2.0/program/soffice.bin

This should then automatically come up with the installer. Please let me know if this works, because i'll be doing it soon.

---

### Post by Ramses de Norre on 2006-03-22
Add this line to your sources: deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./
You can then apt-get the latest open office.org.

---

### Post by pchr on 2006-03-22
I'm using that repository, but I think they provide 2.0.1 rather than 2.0.2.  That might not be a problem, depends on what features you need.

---

### Post by Sef on 2006-03-22
> I'm using that repository, but I think they provide 2.0.1 rather than 2.0.2.

You are correct.

---

### Post by matthewinuk on 2006-03-22
apparentl i dont have permission to move stuff to the /opt folder

---

