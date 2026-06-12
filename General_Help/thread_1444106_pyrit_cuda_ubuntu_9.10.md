---
title: "pyrit cuda ubuntu 9.10"
date: 2010-03-31
forum: General Help
---

### Post by evanuz on 2010-03-31
[FONT=Courier, Monospaced]Hi, i followed the tutorial in order to install pyrit everything went 
 fine but when i hit: 
 'pyrit list_cores' 
  i get this errors: 
  pyrit list_cores 
 Pyrit 0.3.0 (C) 2008-2010 Lukas Lueg [http://pyrit.googlecode.com]("http://www.google.com/url?sa=D&q=http://pyrit.googlecode.com&usg=AFQjCNElKcpOWCJTPxyV217WliN6hJ2VYQ") 
 This code is distributed under the GNU General Public License v3+ 
 [/FONT][FONT=Courier, Monospaced]Traceback (most recent call last): 
   File "/usr/local/bin/pyrit", line 6, in <module> 
     pyrit_cli.Pyrit_CLI().initFromArgv() 
   File "/usr/local/lib/python2.6/dist-packages/pyrit_cli.py", line 
 106, in initFromArgv 
     func(self, **options) 
   File "/usr/local/lib/python2.6/dist-packages/pyrit_cli.py", line 
 237, in list_cores 
     with cpyrit.cpyrit.CPyrit() as cp: 
   File "/usr/local/lib/python2.6/dist-packages/cpyrit/cpyrit.py", line 
 368, in __init__ 
     self.cores.append(CUDACore(queue=self, dev_idx=dev_idx)) 
   File "/usr/local/lib/python2.6/dist-packages/cpyrit/cpyrit.py", line 
 181, in __init__ 
     _cpyrit_cuda.CUDADevice.__init__(self, dev_idx) 
 SystemError: CUDA_ERROR_INVALID_IMAGE 
 [/FONT]
[FONT=Courier, Monospaced]I have cuda 3.0 and a GeForce 9400M 
 What can i do? 
 thanks in advance [/FONT]

---

### Post by evanuz on 2010-04-01
Any advice?? please...

---

### Post by evanuz on 2010-04-01
if anyone wonders i solved it by installing the newest cuda drivers :)

---

### Post by bigchudds on 2010-04-12
hi download the latest nvidia drivers for you card,
also download the cudatoolkit..
exit the x-server screen and install both drivers and toolkit..
log back in and download and install the following:
python-dev , 
build essential, 
zlib, 
openssl, 
libss, 
subversion
from the repositories.
now do as follows and you shouldn't have any problems:
open a terminal and do what follows below:
cd /pyrit 0.3.0
python setup.py build
sudo python setup.py install

open a new terminal

cd /cpyrit 0.3.0
python setup.py build
sudo python setup.py install

then in terminal type pyrit selftest:
pyrit list_cores

this worked for me...hope it helps you

---

