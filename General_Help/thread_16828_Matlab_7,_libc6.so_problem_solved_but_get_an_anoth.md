---
title: "Matlab 7, libc6.so problem solved but get an another one problem"
date: 2005-02-24
forum: General Help
---

### Post by remi.a on 2005-02-24
Hi everyone,

I want to install Matlab 7.0 on Ubuntu Warthy. I have the three CDs.

I have solved a first problem about the libc.so.6 when I want to run the installer :
"/lib/libc.so.6: Permission denied", the solution can be found here :

[http://lists.debian.org/debian-user/2004/11/msg01174.html](http://lists.debian.org/debian-user/2004/11/msg01174.html) 


But now I have a second problem :

I have copied the first CD in a directory of my H.D : /donnees/matlab7install/
and when I run the installer , I have the following error :

**************************************************************************
root@murphy:/donnees/Matlab7install # ./install

Setup aborted . . .
The installer cannot be run when your current directory is on the CD.
Change to the target MATLAB installation directory and rerun the installer.

****************************************************************************

Is someone has solved this problem already ?

Thanks

Remi.

---

### Post by vicent on 2005-03-04
Put CD1 in /media/cdrom and type

            sudo sh /media/cdrom/install

The script install use the sh shell.

---

### Post by vextorspace on 2005-05-24
I did run it as suggested by vicent, but ran into 2 problems.  One was that the drive would not spit out disk 1 when it tells you to put in disk 2.  I just skipped, then re-installed using the next disk.  Then I ran into the problem of the install script, on Ubuntu only as far as I can tell (have seen it work fine on SuSe and Redhat), decides that the matlab base directory is matlab/bin rather than matlab, and it ends up looking for everything in matlab/bin/bin.  I finally went to /lib and did a chmod 755 on the libc-2.3.2.so and reinstalled.  It worked that time.  This libc6 not being allowed to execute has given me problems with many apps.  Is it a security issue?

-Doug

---

### Post by [pl]ice on 2005-05-29
hi, got similar stuff with libc; but i will try this stuff that you have posted it.

for the installation, i had iso's so i mounted them in 3 different dirs, and it worked, u can do that by copying CD's  it into directories, then just point it on the installation.

---

