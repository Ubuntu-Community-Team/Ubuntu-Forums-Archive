---
title: "apt-get error"
date: 2010-06-28
forum: General Help
---

### Post by pythonsyntax on 2010-06-28
root@cyberworld:~# apt-get install mwavem
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  apmd setserial
The following NEW packages will be installed:
  mwavem
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/935kB of archives.
After this operation, 2,707kB of additional disk space will be used.
Selecting previously deselected package mwavem.
(Reading database ... 120407 files and directories currently installed.)
Unpacking mwavem (from .../mwavem_2.0-3ubuntu2_i386.deb) ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Setting up mwavem (2.0-3ubuntu2) ...
MAKEDEV created device node /dev/or .
 * Starting Mwave modem support                                          [fail] 
invoke-rc.d: initscript mwavem, action "start" failed.
dpkg: error processing mwavem (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mwavem
E: Sub-process /usr/bin/dpkg returned an error code (1)


What does this error mean and how do i fix it.

---

### Post by Diabolis on 2010-06-28
Might help:
```
sudo apt-get install -f
```

Maybe is worth reporting it here: [https://bugs.launchpad.net/ubuntu/+source/mwavem/+bug/586800](https://bugs.launchpad.net/ubuntu/+source/mwavem/+bug/586800)

---

### Post by pythonsyntax on 2010-06-28
i did that no luck

---

### Post by Diabolis on 2010-06-28
I can't find the **mwavem** package in the repository, it has been deprecated probably. So, I guess you are using an old version of Ubuntu. You might want to install Ubuntu 10.04 and look for a new package that achieves the same goal.

---

### Post by pythonsyntax on 2010-06-28
they got the same one in 10.04

---

### Post by cloyd on 2010-06-28
It is late here, and I won't be up long this evening, but 

I had a similar error in 10.04 . . .  the interesting thing was, every install, from Synaptic or Ubuntu Software Center displayed the same error. BUT . . . . they all seemed to work. I got rid of that installation, and have recently re-installed 10.04, and this error is not one of my problems, (but I have a few).

Two questions: have you had this error more than once? Is it present in the installation of any other apt? and 
Do the apts work after you install them, even if there was an error? 

The only thing I can add here is, mine did. I think I had an error during install (though I am not sure what happened). I have no solution, but wonder if I shed some light?

---

### Post by bondo101 on 2010-06-28
This command does not work in 9.10 or 10.04 i had someone else on this forum help  that   sudo apt- cache auto clean doesn't work    is garbage  sudo apt cache will come up with all of the commands for the cache. I have gotten a lot of commands from the forums that are garbage. in the mean time i'm learning the command line . I know of only a couple of people on this site that know the proper commands. Please when posting make sure the command will work. were all learning here and its a bitch when you get run around in circles with faulty commands. please leave the version of ubuntu that you are using.
 they say all the commands will work in any version of ubuntu that you have. I don't believe it                             Just my 2 cents worth.:confused:

---

### Post by pythonsyntax on 2010-06-29
Maybe i use the tar file

---

### Post by pythonsyntax on 2010-06-30
Anyone know how to install the tar file for mwavem?

---

### Post by Seanlol on 2010-06-30
> **pythonsyntax said:**
> Anyone know how to install the tar file for mwavem?

Here's a good guide for installing from .tar.gz.

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

### Post by Diabolis on 2010-06-30
[http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092)

---

