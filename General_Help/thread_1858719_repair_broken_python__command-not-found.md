---
title: "repair broken python  command-not-found"
date: 2011-10-12
forum: General Help
---

### Post by kesten on 2011-10-12
Asus 64 bit laptop with Ubuntu 11.04
[FONT=monospace]
I was following a [tutorial]("http://wiki.blender.org/index.php/Dev:2.5/Doc/Building_Blender/Linux/Ubuntu/Scons") on building blender.  This requires installing python3.2  I made a mistake on the symlink and now most new installs and many other commands won't run correctly.  How do i repair the python package management so programs can pick the correct version of python?

Here's what I did...

[/FONT]sudo update-alternatives --install /usr/bin/python python /your/path/to/python3.2 1 
I pointed to /opt/py32/python3.2-3.2 which is the install directory rather than
/opt/py32/python3.2-3.2/bin which is where the built python executable gets put.

Following some generic advice at stack-overflow i tried to remove the symlink with rm /usr/bin/python, 
and re-point it to python3.2 executable with the sudo command above.  This did work, but i think it messes up the package handling pretty 
bad. I recall seeing a warning that update-altenatives was "forcing" something.

kesten@kesten-K42Jr:/etc/alternatives$ dpkg -l python
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version          Description
+++-================-================-================================================
ii  python           2.7.1-0ubuntu5   interactive high-level object-oriented language 

so dpkg thinks we've got python2.7.1 but
kesten@kesten-K42Jr:/etc/alternatives$ which python
/usr/bin/python
kesten@kesten-K42Jr:/etc/alternatives$ ls -l /usr/bin/python
lrwxrwxrwx 1 root root 24 2011-10-11 20:48 /usr/bin/python -> /etc/alternatives/python
kesten@kesten-K42Jr:/etc/alternatives$ ls -l /etc/alternatives/python
lrwxrwxrwx 1 root root 23 2011-10-11 20:48 /etc/alternatives/python -> /opt/py32/bin/python3.2

So the default of typing python gives python3.2.  I can manually use the older version by typing python2.7 at the prompt, but it seems that when programs
call on python they always get python3.2 (since python2.7 is no longer an option -see below?) and this breaks stuff.

When i run
sudo update-alternatives --config python          There are 3 choices for the alternative python (providing /usr/bin/python).    Selection    Path                     Priority   Status ------------------------------------------------------------   
0            /opt/py32/bin             1         auto mode   
1            /opt/py32/bin             1         manual mode   
2            /opt/py32/bin/python3.2   1         manual mode   
3            /opt/py32/python3.2-3.2   1         manual mode  

looks like amnesia for the python2.6, python2.7 that I know exist on the system.  And I think #3 is in error as it is the directory that i 

mistakenly pointed to at the start.  I can now type 

terminal>python and get the interpreter, python3.2,
but typing garbage at the prompt gives error usr/lib/command-not-found
import CommandNotFound no such file or directory Installing programs usually doesn't work because python fails somewher
(looks like wrong version is used).
 
I would like to know what 
$ dpkg -l python 
and 
$ update-alternatives --config python
yield on a system that has python installed correctly.

thanks for any help,

kesten

---

