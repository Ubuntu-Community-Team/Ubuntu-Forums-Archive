---
title: "problem with apt-get in ubuntu terminal(Sourceforge filteration for Iran)"
date: 2010-02-12
forum: General Help
---

### Post by bahareh on 2010-02-12
I should install some packages for a molecular dynamics package(LAMMPS) in Ubuntu 9.10, I have an error and can't do that! 

this is the command line I write: 
"sudo apt-get install build-essential fftw-dev tcsh mpich2 gfortran"

and this is the error:
--2010-02-12 23:49:41--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://sourceforge.net/t7.php](http://sourceforge.net/t7.php) [following]
--2010-02-12 23:49:41--  [http://sourceforge.net/t7.php](http://sourceforge.net/t7.php)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-02-12 23:49:42 ERROR 403: Forbidden.


I know that Sourceforge banned Iran, and I'm an Iraninan citizen.  It seems the error is related to a file named : andale32.exe . I downloaded this file. but I don't know what to do with the file. 
Besides I want to know how to apt-get files from terminal(from sourceforge)? Do I need a proxy? I'm really confused and I'm a beginner in Linux. Please help me...

---

### Post by x33a on 2010-02-12
Take a look here (assuming google search isn't banned, i heard gmail was banned):

[http://www.google.co.in/search?hl=en&q=apt-get+proxy&btnG=Search&meta=&aq=f&oq=](http://www.google.co.in/search?hl=en&q=apt-get+proxy&btnG=Search&meta=&aq=f&oq=)

[http://technoblog.org/2009/07/configure-apt-get-to-use-a-proxy-ubuntu/](http://technoblog.org/2009/07/configure-apt-get-to-use-a-proxy-ubuntu/)

---

### Post by jken146 on 2010-02-12
Perhaps try a different server. System -> Administration -> Software Sources. Pick a server near you.

---

### Post by pcjunkie on 2010-02-12
Best of luck...;)

---

