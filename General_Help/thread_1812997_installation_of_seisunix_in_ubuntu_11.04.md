---
title: "installation of seisunix in ubuntu 11.04"
date: 2011-07-27
forum: General Help
---

### Post by thelastsamurai on 2011-07-27
hi....
i am trying to install seisunix in ubuntu 11.04. the directory is /usr/cwp the makefile is in /usr/cwp/src.
accordingly i have added the following lines in my .bashrc file:

[COLOR=Blue]export CWPROOT=/usr/cwp
export PATH=$PATH:/usr/cwp:/usr/cwp/bin[/COLOR]

but when i try to install the codes by typing "make install" i get the folowing errors:

[COLOR=Red]Installing the CWP codes under the ROOT = /usr/cwp
Continue install? [y/n] y
/usr/cwp
Making necessary directories
mkdir: cannot create directory `/usr/cwp': File exists
mkdir: cannot create directory `/usr/cwp/bin': Permission denied
mkdir: cannot create directory `/usr/cwp/lib': Permission denied
mkdir: cannot create directory `/usr/cwp/include': Permission denied
mkdir: cannot create directory `/usr/cwp/include/Xtcwp': No such file or directory
mkdir: cannot create directory `/usr/cwp/lib/X11': No such file or directory
mkdir: cannot create directory `/usr/cwp/lib/X11/app-defaults': No such file or directory
mkdir: cannot create directory `/usr/cwp/include/Xmcwp': No such file or directory
mkdir: cannot create directory `/usr/cwp/include/Triangles': No such file or directory
mkdir: cannot create directory `/usr/cwp/include/Wpc': No such file or directory
mkdir: cannot create directory `/usr/cwp/include/MGL': No such file or directory
mkdir: cannot create directory `/usr/cwp/include/Reflect': No such file or directory
cd ./cwp; make
make[1]: Entering directory `/usr/cwp/src/cwp'
cd include ; make
make[2]: Entering directory `/usr/cwp/src/cwp/include'
cp: cannot create regular file `/usr/cwp/include/cwp.h': No such file or directory
make[2]: *** [/usr/cwp/include/cwp.h] Error 1
make[2]: Leaving directory `/usr/cwp/src/cwp/include'
make[1]: *** [INSTALL] Error 2
make[1]: Leaving directory `/usr/cwp/src/cwp'
make: *** [cwpstuff] Error 2[/COLOR]
[COLOR=Black]

i tried with sudo make install. i got the following errors:

[COLOR=Red]Makefile:32: /src/Makefile.config: No such file or directory
make: *** No rule to make target `/src/Makefile.config'.  Stop.[/COLOR]
[/COLOR]
can anybody help?
regards....

---

### Post by nothingspecial on 2011-07-27
Hi, is the bit in red your problem?


> 1) read the README's before unbundling cwp_su_all_xx_tar.Z or
  cwp_su_all_xx_tar.gz
2) don't install as 'root' (the superuser) (It is possible to damage
   a system's file structure if the install is not done properly.)

3) begin with the compressed tarfile cwp_su_all_xx_tar.Z or
   cwp_su_all_xx_tar.Z [COLOR="Red"]in some convenient directory that you have
   read and write permission[/COLOR] in that we will call:
   /your/root/path

---

### Post by thelastsamurai on 2011-07-27
thanks for ur reply......i have the unbundled codes within /usr/cwp. i think this is the "convenient directory" that is mentioned in the readme instructions. however if i dont have the read/write permissions in the directory then can u suggest a method to apply the "write" permissions onto that directory?
regards....

---

### Post by nothingspecial on 2011-07-27
Well I generally compile stuff in my home directory. I have /home/source.

Better that than giving yourself rw permissions in /usr

---

### Post by thelastsamurai on 2011-07-27
nope......the same problem persists. this time i tried in the home directory. the result is:


[COLOR=Red]Installing the CWP codes under the ROOT = /home/tanmay/cwp
Continue install? [y/n] y
/home/tanmay/cwp
Making necessary directories
mkdir: cannot create directory `/home/tanmay/cwp': File exists
mkdir: cannot create directory `/home/tanmay/cwp/bin': Permission denied
mkdir: cannot create directory `/home/tanmay/cwp/lib': Permission denied
mkdir: cannot create directory `/home/tanmay/cwp/include': Permission denied
mkdir: cannot create directory `/home/tanmay/cwp/include/Xtcwp': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/lib/X11': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/lib/X11/app-defaults': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/include/Xmcwp': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/include/Triangles': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/include/Wpc': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/include/MGL': No such file or directory
mkdir: cannot create directory `/home/tanmay/cwp/include/Reflect': No such file or directory
cd ./cwp; make
make[1]: Entering directory `/home/tanmay/cwp/src/cwp'
cd include ; make
make[2]: Entering directory `/home/tanmay/cwp/src/cwp/include'
cp: cannot create regular file `/home/tanmay/cwp/include/cwp.h': No such file or directory
make[2]: *** [/home/tanmay/cwp/include/cwp.h] Error 1
make[2]: Leaving directory `/home/tanmay/cwp/src/cwp/include'
make[1]: *** [INSTALL] Error 2
make[1]: Leaving directory `/home/tanmay/cwp/src/cwp'
make: *** [cwpstuff] Error 2
[/COLOR]

---

### Post by thelastsamurai on 2011-07-27
hi......indeed it was the permission problem. make install worked fine. now the problem is with xtinstall. getting the following error:

[COLOR=Red]make xtinstall
cd ./Xtcwp; make
make[1]: Entering directory `/home/tanmay/cwp/src/Xtcwp'
cd include ; make
make[2]: Entering directory `/home/tanmay/cwp/src/Xtcwp/include'
Xtcwp.h installed in /home/tanmay/cwp/include/Xtcwp
Axes.h installed in /home/tanmay/cwp/include/Xtcwp
AxesP.h installed in /home/tanmay/cwp/include/Xtcwp
make[2]: Leaving directory `/home/tanmay/cwp/src/Xtcwp/include'
cd lib     ; make
make[2]: Entering directory `/home/tanmay/cwp/src/Xtcwp/lib'
cc -c -I/home/tanmay/cwp/include -I/usr/X11R6/include -O3 -Wall -Wno-long-long -ansi -pedantic -D_POSIX_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DGNU_SOURCE -DCWP_LITTLE_ENDIAN Axes.c
In file included from Axes.c:72:0:
/home/tanmay/cwp/include/Xtcwp/Xtcwp.h:15:22: fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make[2]: *** [/home/tanmay/cwp/lib/libXtcwp.a(Axes.o)] Error 1
make[2]: Leaving directory `/home/tanmay/cwp/src/Xtcwp/lib'
make[1]: *** [INSTALL] Error 2
make[1]: Leaving directory `/home/tanmay/cwp/src/Xtcwp'
make: *** [xtcwp] Error 2[/COLOR]

---

