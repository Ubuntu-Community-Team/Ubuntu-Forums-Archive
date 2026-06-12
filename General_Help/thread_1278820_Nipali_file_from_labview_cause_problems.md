---
title: "Nipali file from labview cause problems"
date: 2009-09-30
forum: General Help
---

### Post by Daniel Michel on 2009-09-30
I try to install labview 8.5 for linux. packs were .rpm, so I changed them to .deb. and then try to install them.

lots of problem happen while changing them to .deb and while installing.

its ok,I give up on labview, but I want to uninsta[COLOR=Black]l[/COLOR][COLOR=Black]l [nipali_2.1.0-f1_i386.deb]("file:///home/daniel/LabVIEW%25208.5%2520Linux/nipali_2.1.0-f1_i386.deb")

its causing a lot of trouble to the OS, it became a lot slower..[/COLOR]

i try this 
daniel@daniel-desktop:~$ sudo dpkg -i '/home/daniel/LabVIEW 8.5 Linux/nipali_2.1.0-f1_i386.deb'                                                                 
Selecting previously deselected package nipali.                                 
(Reading database ... 217801 files and directories currently installed.)        
Preparing to replace nipali 2.1.0-f1 (using .../nipali_2.1.0-f1_i386.deb) ...
Unpacking replacement nipali ...
/var/lib/dpkg/info/nipali.postrm: 17: Syntax error: Bad for loop variable
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 17: Syntax error: Bad for loop variable
dpkg: error processing /home/daniel/LabVIEW 8.5 Linux/nipali_2.1.0-f1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
/var/lib/dpkg/tmp.ci/postrm: 17: Syntax error: Bad for loop variable
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /home/daniel/LabVIEW 8.5 Linux/nipali_2.1.0-f1_i386.deb

and its also causing trouble with synaptic, and i try to upgrade to ubuntu 9.10, and i couldnt do it because nipali, it said it was going to fix it, but it try to reintall it and couldnt find files..

i dont know what to do. any ideas?

---

### Post by bjordan555 on 2009-11-13
I had a similar issue when installing NIDAQmx 3.2 on my Ubuntu 8.10 box.  After converting the .rpm's the .deb's, per the detailed post [http://ubuntuforums.org/showthread.php?p=6021060](http://ubuntuforums.org/showthread.php?p=6021060), I started installing the deb packages.  When I got to the nepali and nepalki packages, the installer puked, giving me the "bad for loop variable" error that you quoted.  The problem is essentially this:  the script is designed to run in sh, which by default in Ubuntu links to dash, a reduced instruction set shell. The syntax of the for loops used in the postinst script for these packages doesn't work with dash, and it fails on line 158. To solve this, I linked sh directly to bash instead of dash, which solves the problem.  Both packages install now.  

Next, we'll see if I get my device to be recognized.

Hope this helps you. 

Ben

---

