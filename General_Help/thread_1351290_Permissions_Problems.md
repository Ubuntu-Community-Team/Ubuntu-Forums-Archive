---
title: "Permissions Problems"
date: 2009-12-10
forum: General Help
---

### Post by jfarrar4 on 2009-12-10
[B][SIZE=3]I am having a problem with permissions when I try to run MAT (gene-chip analysis software) on a 9.10 x64.

After a few snags, the programs compiled and installed easily enough using the default installation:[/SIZE][/B]

[http://liulab.dfci.harvard.edu/MAT/](http://liulab.dfci.harvard.edu/MAT/)
[SIZE=2]
[COLOR=black][FONT=Arial]The information here is intended to assist          you in installing MAT from source code. Since MAT uses Python's          distutils, this should be a fairly automatic process. We have          successfully installed MAT on several platforms including Linux-x86,          Linux-AMD64, Solaris-AMD64, Mac OSX and Windows Vista. We usually          recommend 2 Gb memory for the whole genome tiling array data analysis.         

[/FONT][/COLOR][/SIZE]         **[SIZE=2]_[B][FONT=Arial]MAT Build Dependencies[/FONT]**_[/SIZE][/B]

         
[LIST=1]
[*]                          [SIZE=2][FONT=Arial]              [/FONT][/SIZE][FONT=Arial][SIZE=2][Python             ]("http://www.python.org/")>= 2.4 with module             [             numarray ]("http://www.stsci.edu/resources/software_hardware/numarray")>= 1.3.2; [/SIZE][/FONT]
[*]                          [SIZE=2][FONT=Arial]              [/FONT][/SIZE][FONT=Arial][SIZE=2]gcc/g++ >=              3.2.2[/SIZE][/FONT]
[*]                          [SIZE=2][FONT=Arial]              [/FONT][/SIZE][FONT=Arial][SIZE=2][SWIG ]("http://www.swig.org/")             >= 1.3.24
             [/SIZE][/FONT]
[/LIST]
         **         [SIZE=2]_[FONT=Arial]Brief Install Process from Source          Code ([/FONT]_[FONT=Arial]Thank Giles Hall for the          installation script!)[/FONT][/SIZE]**

         
[LIST=1]
[*]             [FONT=Arial][SIZE=2]Download the             [MAT source code]("http://liulab.dfci.harvard.edu/MAT/Download.htm") and install/upgrade the              dependencies listed above if necessary [/SIZE][/FONT]
[*]             [FONT=Arial][SIZE=2]tar xzvf MAT-xxx.tar.gz[/SIZE][/FONT]
[*]             [FONT=Arial][SIZE=2]cd MAT-xxx[/SIZE][/FONT]
[*]             [FONT=Arial][SIZE=2]Do a default              installation :
    python setup.py install 
            This will try to install MAT in python's site-packages directory and              even install the command "MAT" in your bin directory.
 [/SIZE][/FONT]
[*]             [FONT=Arial][SIZE=2]For more              flexibility (if you need to do a "user" level install):
    python setup.py  install  --home=<dir>
            which will install MAT under <dir>/lib/python/MAT and the command              "MAT" in <dir>/bin. Since you picked <dir>, you need to add              <dir>/bin to your PATH and set the python library search path: 
    setenv PYTHONPATH "<dir>/lib/python:$PYTHONPATH"
            This command will need to be repeated each time you login, thus you              may want to add this command to your .cshrc script in your home              directory.
 [/SIZE][/FONT]
[*]             [FONT=Arial][SIZE=2]Enjoy MAT[/SIZE][/FONT]
[/LIST]
**[SIZE=3]However, when I run MAT, I get a directory permissions error that doesn't make sense to me:[/SIZE]**

jason@jason-laptop:~$ cd ~/Desktop/MAT/scripts
jason@jason-laptop:~/Desktop/MAT/scripts$ MAT test.tag
/usr/local/lib/python2.6/dist-packages/MAT/FileIO.py:5: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import sys, time, os.path, AffyFileParser, re, ConfigParser, zipfile, os, md5
[ Thu Dec 10 13:07:58 2009 ]
Tag file format error:  <type 'exceptions.Exception'> No write access to the cel folder /home/jfarrar4/Desktop/CEL/. Please either change the directory access permission or hard link(or copy) your cel files to a writable directory
jason@jason-laptop:~/Desktop/MAT/scripts$ 

**[SIZE=3]Regardless of where I move these files or how I set folder permissions, I get this error.  Currently this whole directory appears to have unrestricted access:[/SIZE]**

jason@jason-laptop:~$ ls -l ~/Desktop
total 16
-rw-rw-rw- 1 jason jason 2172 2009-04-23 23:15 20090423JR2.tag~
drwxrwxrwx 2 jason jason 4096 2009-12-10 12:17 CEL
drwxrwxrwx 2 jason jason 4096 2009-12-10 11:43 Data
drwxrwxrwx 4 jason jason 4096 2009-07-31 15:14 MAT
jason@jason-laptop:~$ ls -l ~/Desktop/MAT/scripts
total 234880
-rw-rw-rw- 1 jason jason 120190765 2009-11-17 20:28 JFar-Meth-1M.CEL
-rw-rw-rw- 1 jason jason 120300148 2009-11-17 20:31 JFar-Meth-1T.CEL
-rwxrwxrwx 1 jason jason      3588 2009-07-31 13:36 MAT
-rwxrwxrwx 1 jason jason       983 2009-04-24 14:07 MatRep
-rw-rw-rw- 1 jason jason      2105 2009-12-10 11:43 test.tag
jason@jason-laptop:~$ 

**[SIZE=3]Does anyone have any suggestions or ideas as to where the problem may be?[/SIZE]**

---

### Post by registering on 2009-12-10
I'm not sure your problem is related to Ubuntu, so you might get better help elsewhere, but what are the permissions on /home/jfarrar4/Desktop/CEL/.? It's unclear the Desktop folder you're showing is the above path.

---

