---
title: "trying to install gcc3.4 from downloaded tar"
date: 2006-04-08
forum: General Help
---

### Post by piccolo solo on 2006-04-08
Hi folks
To install my LAN and audio drivers I need gcc version 3.4 (version 4 is on my installation). I cannot use apt-get cos I cannot get online. Also v3.4 not on install CD.

I've downloaded v3.4 from gcc but am stuck with how to install from this. I am new to all this and would be really grateful for guidance so that I can get online and sort everything else out.

I don't expect to be spoon fed forever, but I have been stuck with this for 3 days.

thanks
Picc

---

### Post by arkangel on 2006-04-08
If I remember well the  gcc-3.4 comes with the cd , try to install it via synaptic
search for gcc 3.4  

then  most probably  when installing  new hardware or compile somethign new   you will have an error that tells you  gcc-3.4  not found ,  before running   the configure file  set CC to  gcc 3.4 
$ set CC=/usr/bin/gcc-3.4

---

### Post by arkangel on 2006-04-08
if you have the tar  extract it 
$ tar -xvf gcc....tar
go to the directory  
$ ./configure  
$ make 
$sudo make  install

if you are luky all will be ok :-k

---

### Post by piccolo solo on 2006-04-08
thanks arkangel
3.4 doesnt seem to be on the CD (burned from downloaded ISO)

have tried similar instructions - will try yours now
thanks for replying

Picc

---

