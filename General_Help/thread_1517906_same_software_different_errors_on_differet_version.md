---
title: "same software different errors on differet versions of UBUNTU and different PCs"
date: 2010-06-25
forum: General Help
---

### Post by dieter-erich on 2010-06-25
Hi,
I  compiled a scientific program suite (bsoft) on four PCs without errors. However, when running one of the programs (bshow, a graphics application involving Tcl/Tk libraries) it issues an error message on three of them (UBUNTU 10.04) and exits. It runs smoothly on one (UBUNTU 9.4). At least the Tcl/Tk libraries are the same versions. How can I find out what is wrong? Clearly,the versions of all the installed packages and libraries are not the same. Can this be the reason? 
 
In order to follow up, I made a virtual machine and installed UBUNTU 9.04. Again compilation was fine but on running the program I received still another, **completely different error message** and it crashed. 
  
Can anybody tell me whether it is possible that a given software just runs on a particular version of UBUNTU on a particular type of PC? I am somewhat desperate. I cannot try all versions of UBUNTU and the various files from the corresponding libraries to find out what is required for correct compilation/running. 
 
Hints are greatly appreciated! 
D-E

---

### Post by dcstar on 2010-06-26
> **dieter-erich said:**
> Hi,
I  compiled a scientific program suite (bsoft) on four PCs without errors. However, when running one of the programs (bshow, a graphics application involving Tcl/Tk libraries) it issues an error message on three of them (UBUNTU 10.04) and exits. It runs smoothly on one (UBUNTU 9.4). At least the Tcl/Tk libraries are the same versions. How can I find out what is wrong? Clearly,the versions of all the installed packages and libraries are not the same. Can this be the reason? 
 
In order to follow up, I made a virtual machine and installed UBUNTU 9.04. Again compilation was fine but on running the program I received still another, **completely different error message** and it crashed. 
  
Can anybody tell me whether it is possible that a given software just runs on a particular version of UBUNTU on a particular type of PC? I am somewhat desperate. I cannot try all versions of UBUNTU and the various files from the corresponding libraries to find out what is required for correct compilation/running. 
 
Hints are greatly appreciated! 
D-E

Posting the error messages may give those who aren't mind-readers some chance of assistance.

---

### Post by dieter-erich on 2010-06-26
Hi David,
  sorry, but at this stage, my question was meant to be rather general. Effectively, it is the bash script bshow.sh attached that causes the errors:

Error messages:

UBUNTU 9.4
none - runs without problems

UBUNTU 10.04 LT
Error in startup script: invalid command name "fileType"
    while executing
"fileType $filename"
    invoked from within
"set file_type [fileType $filename]"
    (file "/usr/local/bsoft/bin/bshow" line 451)

UBUNTU 9.04
Error in startup script: can't read "Bsoft": no such variable
    while executing 
"string length $Bsoft"
    invoked from within
"if { [string length $Bsoft] < 2 } {
    puts "Environmental variable BSOFT not found: Set to /usr/local/bsoft"
    set Bsoft /usr/local/bsoft
}"
    (file "/usr/local/bsoft/bin/bshow" line 61)
-------------------------------------------
I suspect that it is the installed version of bash that leads to these errors. E.g. 3.2-5 ubuntu1 where it works, and 4.0-5ubuntu2 where it gives one of the error messages shown above for 10.04. Could that be? Clearly, although I set the environment variables and path etc. exactly the same, many packages other than bash will differ.

How to find out whats wrong??

Thanks D-E

---

### Post by dieter-erich on 2010-07-05
The issue is solved: I installed Centos 5.4 in a virtual machine and the software compiled and run without problems. Has anybody had similar issues, i.e. software not correctly compiling (and/or running) under UBUNTU but running under another Linux clone? It might be interesting to find the reason for this!
D-E

---

### Post by Meskarune on 2010-07-05
"Has anybody had similar issues, i.e. software not correctly compiling (and/or running) under UBUNTU but running under another Linux clone?"

That is why I stopped using ubuntu. Other linux distributions don't have problems where ubuntu does.

---

### Post by AleksKeaton on 2010-07-05
Ubuntu isn't a mind reader either. Maybe that is the problem. Try being more specific about your variables, and don't just use a workaround like switching version. Show some loyalty, man!

---

### Post by dieter-erich on 2010-07-05
Hi AleksKeaton,
 
Nobody and nothing needs to mindread :-)! Here are the details: I spent hours and hours trying to correctly install Auto3DEM ([http://cryoem.ucsd.edu/programs-auto3dem-archive.shtm](http://cryoem.ucsd.edu/programs-auto3dem-archive.shtm)) so that the component robEM would run. On some older UBUNTU versions I got a lot of (different) compiler errors (eg. 'NO OP' or 'missing sentinel'). This occured on two different laptops, one desktop, and one virtual machine. For example, out-truncated.txt (for forum limitation reasons) and out1.txt are such compiler outputs.
 
On UBUNTU 10.04 everything appeared to compile fine and without any error message. However, when I invoked robem I got a 'buffer overflow' message and a crash of the program (see attached robem.txt). 
 
I then made a virtual machine and installed Centos 5.4. Robem compiled and run out of the box. So, what is wrong? I would very much like to understand what is going on here and would be happy to get a solution. I liked UBUNTU very much when starting to experiment with linux but now I got some doubts......
 
Best and thanks for hints, D-E

---

### Post by dieter-erich on 2010-08-28
Issue solved! See my other post on auto3dem!

---

