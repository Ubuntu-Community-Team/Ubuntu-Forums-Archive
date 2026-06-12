---
title: "Installing FEA software (Salome+Code-Aster) in Breezy"
date: 2006-03-30
forum: General Help
---

### Post by jmb365 on 2006-03-30
Hello all,

I wondered if anybody has had success installing a Finite Element Analysis (FEA) Pre/Post processor package called Salome (2.2.8) in Breezy or even Hoary for that matter.  I have run into some stumbling blocks.  I am successfully using it on a RedHat Fedora Core 3 (RH FC3) machine however.

See Salome at "http://www.salome-platform.org"  If you have not looked at this FEA software, I strongly urge you to.  It is the most feature laden GPL'ed FEA software I have seen so far!  I have dabbled with Calculix (cgx - which is good because of capability to use an ABAQUS style input deck for the ccx -solver) but I think just the GUI based geometric tools of Salome make it a superior product.  Tutorials & Docs are available in English.

I have compiled Code-Aster (Ver 8.2) the companion FEA solver in Breezy with some minor tweaking (search for "salome" or "Code_Aster" in these forums).  Cons: Online docs are mostly in French.

Hope to hear from somebody out there who uses this kind of stuff!

JMB

---

### Post by jmb365 on 2006-04-04
Hello,

I have made some progress installing Salome (2.2.8) in "Breezy" but I am running into a version problem with Python modules.  For which I am hoping some gurus here might have some clues.  I know, I am crawling out onto some uncharted (bleeding edge) domain here, but that is the spirit of open software, isn't it?

This is what I have so far:

# cd /tmp
# gunzip -cd /home/LinuxDownLoads/FEA/salome/salome-2.2.8.tar.gz | tar -xvf -
# cd SALOME-2.2.8/
# ./runInstall -b -f config_RedHat_8.0.xml -t /usr/local/bin/salome

(There are messages that the documentation cannot be installed because "epstopdf" or "latex" cannot be found, but that is not my main problem)

Then I followed the recommendations (based on notes from somebody else) for installation on a Debian based distro as shown below: 
-----------------------------------
I used the configuration file for RedHat 8.0 installation and that seems to work OK on Debian
The only thing that was necesary to do is the following (at least on Debian Testing).

# ./runInstall -b -f config_RedHat_8.0.xml -t /usr/local/bin/salome

After the installation is finished do the following.
# cd /usr/local/bin/salome/KERNEL_2.2.8
# cp salome.sh salome.sh.orig
# gedit salome.sh &
In the KERNEL_2.2.8 directory there is a file called salome.sh that sets up the enviroment variables, in that one, the second source line has to be changed as follows.

 out_var='echo $1 $2 |  awk -W sprintf=5060 -v dir=$3 '{       \

(JMB: because the default sprintf runs out of space or something, I presume)
------------------------------------------------------------------
Then set up the environment variables:
root@ubuntu:/usr/local/bin/salome/KERNEL_2.2.8# source salome.sh
(JMB: No problems so far....)

root@ubuntu:/usr/local/bin/salome/KERNEL_2.2.8# /usr/local/bin/salome/KERNEL_2.2.8/bin/salome/runSalome

But, when I run this command I get the errors shown below:
(It appears there are Python C API mismatches between Salome's modules & the Python version of a stock "Breezy" with updates platform. Any suggestions or hints from anybody would be welcome here...)

Searching for a free port for naming service: 2810 - Ok
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy: This Python has API version 1012, module _omnipy has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.orb_func: This Python has API version 1012, module _omnipy.orb_func has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.poa_func: This Python has API version 1012, module _omnipy.poa_func has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.poamanager_func: This Python has API version 1012, module _omnipy.poamanager_func has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.omni_func: This Python has API version 1012, module _omnipy.omni_func has version 1011.
  import _omnipy
omniORB: Assertion failed.  This indicates a bug in the application using
omniORB, or maybe in omniORB itself. e.g. using the ORB after it has
been shut down.
 file: omni30/omnipy.cc
 line: 396
 info: PyClass_Check(omniPy::pyWorkerThreadClass)
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy: This Python has API version 1012, module _omnipy has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.orb_func: This Python has API version 1012, module _omnipy.orb_func has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.poa_func: This Python has API version 1012, module _omnipy.poa_func has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.poamanager_func: This Python has API version 1012, module _omnipy.poamanager_func has version 1011.
  import _omnipy
/usr/local/bin/salome/omniORB-3.0.5/lib/python/omniORB/__init__.py:142: RuntimeWarning: Python C API version mismatch for module _omnipy.omni_func: This Python has API version 1012, module _omnipy.omni_func has version 1011.
  import _omnipy
omniORB: Assertion failed.  This indicates a bug in the application using
omniORB, or maybe in omniORB itself. e.g. using the ORB after it has
been shut down.
 file: omni30/omnipy.cc
 line: 396
 info: PyClass_Check(omniPy::pyWorkerThreadClass)
/usr/local/bin/salome/KERNEL_2.2.8/bin/salome/runSalome: line 40: 28043 Aborted                 python ${KERNEL_ROOT_DIR}/bin/salome/runSalome.py
root@ubuntu:/usr/local/bin/salome/KERNEL_2.2.8#

---

### Post by jmb365 on 2006-04-06
Solome-2.2.8 is running on Ubuntu Breezy!

Finally I did it with some help from good folks at Salome & Code-Aster forums.  Here are the steps to installing Salome-2.2.8:

# cd /tmp
Download salome-2.2.8.tar.gz to /tmp from their website using any browser

# gunzip -cd /home/LinuxDownLoads/FEA/salome/salome-2.2.8.tar.gz | tar -xvf -
# cd SALOME-2.2.8/

# ssh -X root@localhost		
(Do this if you are just a normal user, "su - " will NOT work since it cannot use display:0)

# ./runInstall -g
(Install in /usr/local/bin/salome, using the GUI interface,
and configure it to use all binaries, wherever possible)
 - Launch the installation procedure.
 - In the second page "install settings" click on the button "more"
 - In the new page select "install binaries" for each product, each time it's possible.
 - click on "next" and continue the installation

After the installation is finished the salome.sh script needs to be modified.
# cd /usr/local/bin/salome/KERNEL_2.2.8
# cp salome.sh salome.sh.orig
# gedit salome.sh &
(In the KERNEL_2.2.8 directory there is a file called salome.sh that sets up the enviroment variables, where, the second source line has to be changed as follows:)

  out_var='echo $1 $2 |  awk -W sprintf=5060 -v dir=$3 '{       \
or if you get error: "awk: option `-W sprintf=5060' unrecognized, ignored" change awk to mawk, when you run "source salome.sh" change it such:
  out_var='echo $1 $2 |  mawk -W sprintf=5060 -v dir=$3 '{      \

Then you can do (in the KERNEL_2.2.8 directory)
# source salome.sh

Some lib errors can fixed by:
# ln -s /usr/lib/libssl.so.0.9.7 /usr/lib/libssl.so.2
# ln -s /usr/lib/libcrypto.so.0.9.7 /usr/lib/libcrypto.so.2
Error: Does not find libdps.so.1, 
The fix is to get Hoary's libdps1 package, since a Breezy pacakge is not available
# cd /tmp
# wget -nd [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/libdps1_6.8.2-10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/libdps1_6.8.2-10.1_i386.deb)
# sudo dpkg -i libdps1_6.8.2-10.1_i386.deb

And Run Salome by:
# /usr/local/bin/salome/KERNEL_2.2.8/bin/salome/runSalome &

I have tried this process on two different PCs running "Breezy" and it works.  I have not tested all the functions of this setup, but hope to in the near future.  Will keep you all posted.

Enjoy! 
JMB

---

### Post by Fingolfin on 2006-07-30
Unfortunately, many users report problems when installing Salome. Maybe for these reasons we need a dedicated distribution like Scientific Linux where all the core applications will work immediately after the installation. (Scibuntu?)

---

### Post by NeiNastran on 2008-02-08
Interesting, have you looked into other FEA software for Linux? What other apps have you come across?

---

