---
title: "Installed program, wrong way?  How to remove?  [Firebird db]"
date: 2012-09-23
forum: General Help
---

### Post by n1cehat on 2012-09-23
Hey howzitgoing?  I set up an Ubuntu server and installed a whole bunch of apps.  They are all necessary for the website we are migrating over there.  I installed everything from apt-get, but there was a program or two that it couldn't find.  

Not knowing how to add repositories into Ubuntu, I went and got the source files, compiled, and installed.  

Now the other developer says it is incorrectly installed, and we need to get it out of there somehow so we can properly install it (once it is added to the repository).

This is what I did to install it:

```
cd /home/myhomefolder
mkdir firebird203
cd firebird203/
wget http://downloads.sourceforge.net/firebird/FirebirdSS-2.0.3.12981-1.amd64.tar.gz
tar -xvf FirebirdSS-2.0.3.12981-1.amd64.tar.gz
cd FirebirdSS-2.0.3.12981-1.amd64
./install.sh

```

How do I get it to a state where it was like I never put it in there in the first place?  

Your help is extremely helpful!  I searched and searched and couldn't find anything, asking is a last resort!  Whatever the answer happens to be, the method will be learned as I could foresee this problem coming up in the future.

Thanks!

---

### Post by Cheesemill on 2012-09-23
Have you tried running the uninstall script?

I've just had a quick look at the install script for you and it seems to create an uninstall script in /opt/firebird/bin

---

