---
title: "MATLAB install error... :("
date: 2010-03-01
forum: General Help
---

### Post by wannabegeek on 2010-03-01
Good evening or day...

I have an ISO image of MATLAB that I would like to install and have been having a little trouble.

1)First I made a mount point for the ISO on ~/Desktop
2)Then, extracted the .zip into the mountpoint directory.
3)Copied the license.dat into /usr/local/matlab7.
4)Changed dir. into /usr/local/matlab7 and sudo /full/path/./install
5)I'm then supposed to modify my license.txt file and put it in $MATLAB/etc

At 4) I received the error:
Error writing to /tmp/26599tmwinstall
The installer is unable to copy files to /tmp.
Make sure that /tmp exists, is writable, and has
at least 5 megabytes of available space.

/tmp exists and has +w 

I'm dying to get this installed so I can work on my research project at home...thanks in advance,

wbg

---

### Post by wannabegeek on 2010-03-02
Replying to self...

I got matlab installed, using command from Linuxforums
$./install -glnx86 -nocp

now I  can't get it to start, tried $matlab just about everywhere and $./matlab

anyone ?

---

### Post by r_s on 2010-03-02
enter the matlab directory , in your case
cd /usr/local/matlab7 
cd bin
./matlab

---

### Post by wannabegeek on 2010-03-02
Thanks, cd into bin did something !!

I received the following error:
[PHP]Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------

    matlab: No MATLAB bin directory for this machine architecture.

           ARCH = glnxa64

[/PHP]

---

### Post by r_s on 2010-03-02
Have a look at this thread
[http://ubuntuforums.org/archive/index.php/t-1194045.html](http://ubuntuforums.org/archive/index.php/t-1194045.html)

---

