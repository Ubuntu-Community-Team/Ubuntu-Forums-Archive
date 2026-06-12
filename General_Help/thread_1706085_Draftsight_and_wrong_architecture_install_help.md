---
title: "Draftsight and wrong architecture install help"
date: 2011-03-13
forum: General Help
---

### Post by Biciclettapc on 2011-03-13
Trying to install draftsight on my 64 bit 10.10 system to give it a try.  

I do solid modeling work for a living (Inventor/Solidworks) and have to use Autocad.  Ran across this program a month or so ago and really like it.  Much less bloated that AC but does a nice job in the 2d world for a basic program.

The package installer gives me a wrong architecture message (see attached)
I think I had to change that to get adobe AIR installed and wonder if its possible to do the same here.

I am pretty much a noob in linux command line, which I soon to hopefully begin to learn.

Thanks
Paul

---

### Post by PereUbu on 2011-03-13
I tried this and it worked:


Install the two missing dependencies first:
(Copy and paste the following commands in to your terminal)
> sudo apt-get install libxcb-render-util0

Press enter and enter your password if asked

> sudo apt-get install libdirectfb-extra

Press enter and enter your password if asked


Move your DraftSight.deb file to your home folder (/home/yourusernamehere)
 
Then you have to force install the DraftSight package:
(Copy and paste the following command in to your terminal)
> sudo dpkg -i --force-architecture DraftSight.deb

Press enter and enter your password if asked

Hope this will work for you, too!

---

### Post by Biciclettapc on 2011-03-13
Pere

Sweet, worked great on install, Thank You!

Paul

---

### Post by kris kincaid on 2011-03-29
I'm trying to get Draftsight working on my AMD64 machine, and am running into an error. I followed the procedure posted above, and I get this error:



```
user@ubuntu-AMD64:~/Downloads$ sudo dpkg -i --force-architecture DraftSight.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libexpat1 (>= 2.0.1-4)
dpkg: error processing DraftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 DraftSight.deb
```

The version of libexpat1 I have installed is 2.0.1-7ubuntu3, which is the latest in the repository. Do you think the "ubuntu3" tacked on the end of the filename is the issue?

I'm using 11.04 with an AMD64 processor. Thanks :)

---

### Post by kris kincaid on 2011-03-30
Just bringing this TTT. I tried installing the Debian version of libexpat1 ([Debian version 2.0.1-7]("http://packages.debian.org/sid/libexpat1")) and still get the same results as above.

Anybody have any ideas that I could try? Thanks! :)

---

### Post by Biciclettapc on 2011-03-30
Kris,

Might start a new thread..... 

Paul

---

### Post by alejandr on 2011-04-04
> **Biciclettapc said:**
> Pere

Sweet, worked great on install, Thank You!

Paul
PereUbu
I did as you said and all was fine until I began installation:
I get this error:
sudo dpkg -i --force-architecture DraftSight.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 176357 files and directories currently installed.)
Unpacking dassault-systemes-draftsight (from DraftSight.deb) ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
**/var/lib/dpkg/tmp.ci/preinst: line 21: /var/lib/dpkg/tmp.ci/ShowLicence: No such file or directory**
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
dpkg: error processing DraftSight.deb (--install):
 subprocess new pre-installation script returned error exit status 127
Errors were encountered while processing:
 DraftSight.deb
Any Ideas on how to solve this?
I can't get it working. and I need it
Many thanks in advance.

---

### Post by player107 on 2011-04-10
hello
I've installed it on my sony VPCYB1 which is AMD and with ubuntu 64bits
I ve no pb, no add lib to install etc. 
The procedure is :
unpack the draftsight file in some directory (ex : DS), 
then copy the DS/opt/ and DS/var/  to /opt and /var
then go to  DS/DEBIAN
then sudo ./preinst
then sudo ./postinst
then a menu should have been created in the graphical ubuntu menu : you can launch it

The only pb I have is that the draftsight graphical frame is blinking when I move the screen over it : so I cannot use it. If some one could help me it would be great

thanks
Emmanuel

---

### Post by claverias on 2011-05-09
> **player107 said:**
> hello
I've installed it on my sony VPCYB1 which is AMD and with ubuntu 64bits
I ve no pb, no add lib to install etc. 
The procedure is :
unpack the draftsight file in some directory (ex : DS), 
then copy the DS/opt/ and DS/var/  to /opt and /var
then go to  DS/DEBIAN
then sudo ./preinst
then sudo ./postinst
then a menu should have been created in the graphical ubuntu menu : you can launch it

The only pb I have is that the draftsight graphical frame is blinking when I move the screen over it : so I cannot use it. If some one could help me it would be great

thanks
Emmanuel
Hello player107. Try:
sudo apt-get install libdirectfb-extra
sudo apt-get install libxcb-render-util0

Thanks for your advice.

---

### Post by bad_cables on 2011-05-23
thanks guys!! worked great. 

what an awesome app to have in linux! now i can show off my new desktop at work and seriously bruise my boss's ego!

cheers!! 


PS: draftsight is pro++

---

### Post by knezmej on 2011-07-06
You can try install _libc6 for i386_ (simultaneously to already installed libc6 for amd64) *from synaptic*. I guess it helps in my case.

---

### Post by LordNodens on 2011-07-11
> **player107 said:**
> hello
I've installed it on my sony VPCYB1 which is AMD and with ubuntu 64bits
I ve no pb, no add lib to install etc. 
The procedure is :
unpack the draftsight file in some directory (ex : DS), 
then copy the DS/opt/ and DS/var/  to /opt and /var
then go to  DS/DEBIAN
then sudo ./preinst
then sudo ./postinst
then a menu should have been created in the graphical ubuntu menu : you can launch it

The only pb I have is that the draftsight graphical frame is blinking when I move the screen over it : so I cannot use it. If some one could help me it would be great

thanks
Emmanuel

Thanks a lot! This worked! No problems at all! Ubuntu 11.04 64bit

---

### Post by phillip.toone on 2011-07-18
For what it is worth I had to install sendmail to get Draftsight to install.  I'm going to remove sendmail in a few days and see if it breaks Draftsight.  Also, I will be comparing Draftsight to Hycad via wine since that is what I have been using to deal with dxf files.  Now I should be able to deal with dwg files.  Also, I am a SolidWorks user via VirtualBox.  Chow!

---

