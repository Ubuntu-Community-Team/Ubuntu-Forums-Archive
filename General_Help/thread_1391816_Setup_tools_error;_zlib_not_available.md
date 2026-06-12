---
title: "Setup tools error; zlib not available"
date: 2010-01-27
forum: General Help
---

### Post by placrsaeed on 2010-01-27
Hi All,

I am trying to install Trac([http://trac.edgewall.org/](http://trac.edgewall.org/)) on Ubuntu Karmic Koala. In order to install Trac, setup tools needs to be installed.

I have followed the instructions on this page; [http://trac.edgewall.org/wiki/setuptools](http://trac.edgewall.org/wiki/setuptools) but when I run the 'python ez_setup.py' command I get the following error message
'Traceback (most recent call last):
  File "ez_setup.py", line 278, in <module>
    main(sys.argv[1:])
  File "ez_setup.py", line 212, in main
    from setuptools.command.easy_install import main
zipimport.ZipImportError: can't decompress data; zlib not available
root@placraa1:~/Downloads/Trac-0.11.6# zlib
-bash: zlib: command not found'

Any ideas on how to fix this? I am new to Linux so any help is greatly appreciated.

Saeed.

---

### Post by mhgsys on 2010-01-27
when I (running ubuntu 9.04) type ```

apt-cache search zlib | less 
```

I found zlib1g - compression library - runtime

So.;; 

I guess all you should do is ```

sudo apt-get install zlib1g 
```

---

### Post by placrsaeed on 2010-01-27
Thanks Mhgsys for replying so quick.

I just tried that but it seems like it is already installed as I got the following message;
root@placraa1:~/Downloads/Trac-0.11.6# sudo apt-get install zlib1g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Nonetheless I did try to install setup tools again but it threw the same error as before.

Saeed

---

### Post by khelben1979 on 2010-01-27
Maybe you need zlib-dev package?

---

### Post by placrsaeed on 2010-01-27
Just tried:

sudo apt-get install zlib-dev

But got the following message:
'root@placraa1:~/Downloads/Trac-0.11.6# sudo apt-get install zlib-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zlib-dev'

---

### Post by mhgsys on 2010-01-27
to get the dev package it would be 
```

sudo apt-get install zlib1g-dev 

```

By the way.; come to think of it. 

I guess maybe you need zlibc 

```
sudo apt-get install zlibc
```

---

### Post by placrsaeed on 2010-01-27
I tried that too...it returned the same message;

root@placraa1:~/Downloads/Trac-0.11.6# sudo apt-get install zlib1lg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zlib1lg-dev

---

### Post by placrsaeed on 2010-01-27
Installing zlibc gives the following message;

root@placraa1:~/Downloads/Trac-0.11.6# sudo apt-get install zlibc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlibc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by mhgsys on 2010-01-27
> **placrsaeed said:**
> I tried that too...it returned the same message;

root@placraa1:~/Downloads/Trac-0.11.6# sudo apt-get install zlib1lg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zlib1lg-dev

Thats because you have a typo; 

it's not zlib1lg-dev it's zlib1g-dev

---

### Post by placrsaeed on 2010-01-27
Thanks for pointing that out; however it returns the following;

root@placraa1:~/Downloads/Trac-0.11.6# sudo apt-get install zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g-dev is already the newest version.
zlib1g-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by mhgsys on 2010-01-27
reading the setup page you are following. 


setuptools include "easy_install" script for convenient installation of packages found on  Python Package Index including Trac with all necessary dependencies. 


[http://pypi.python.org/pypi/setuptools/](http://pypi.python.org/pypi/setuptools/)

edit: I really gotta go (parents in law are waiting for me ) Good luck with it, and there will be (hopefully) more people to support you,

---

### Post by placrsaeed on 2010-01-27
I tried to install Trac this way initially and this is how I first came accross the zlib error. Nonetheless I just tried it again by downloading the egg file and running it with the command:
```
root@placraa1:~/Downloads# sudo sh setuptools-0.6c11-py2.6.egg

```and it still gives the same error...
```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
zipimport.ZipImportError: can't decompress data; zlib not available
```Thanks for taking your time to help me. Appreciate it.

---

### Post by mhgsys on 2010-01-27
(I'm so late man, haha) 

Follow up the proper links to easy install. 


[http://peak.telecommunity.com/DevCenter/EasyInstall](http://peak.telecommunity.com/DevCenter/EasyInstall)

---

### Post by placrsaeed on 2010-01-27
I've came accross that website previously, it directed me to the PyPi page for the egg download. I'm not sure where I can go from here.

Nonetheless Thanks for your time and help Mhgsys.

---

### Post by mhgsys on 2010-01-27
I'm gonna try this out for you on my own computer (tomorrow perhaps) so I can provided you with more info on this. 

However I'm booting 9.04 so maybe it will be slightly different, or maybe I will not receive the same error.
 
However , I will try 


In the meantime with this writing I would also like to !BUMP! for other users to get in this thread as well.

;)

---

### Post by mhgsys on 2010-01-28
I was wondering;
What is the output from ```
python
``` on your machine?


and (in the same terminal you've just typed python) what happens when you ```
import zlib
``` and do ```
zlib.__version__
```

I'm using Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
zlib.__version__
'1.0'


 Here's what I did on Ubuntu 9.04;

First i downloaded Track from [http://trac.edgewall.org/wiki/TracDownload](http://trac.edgewall.org/wiki/TracDownload)

I got the Trac-0.11.6.tar.gz and I extracted it by simply clicking it,.

then i got the Setuptools with

```
wget http://peak.telecommunity.com/dist/ez_setup.py
```

Which gave me ```
wget http://peak.telecommunity.com/dist/ez_setup.py
--2010-01-28 18:17:50--  http://peak.telecommunity.com/dist/ez_setup.py
Resolving peak.telecommunity.com... 209.190.5.234
Connecting to peak.telecommunity.com|209.190.5.234|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10285 (10K) [text/plain]
Saving to: `ez_setup.py'
100%[======================================>] 10,285      37.3K/s   in 0.3s    

2010-01-28 18:17:51 (37.3 KB/s) - `ez_setup.py' saved [10285/10285]

```



Then I runned

```
sudo python ez_setup.py
```

wich gave me ```

Downloading [http://pypi.python.org/packages/2.6/s/setuptools/setuptools-0.6c11-py2.6.egg](http://pypi.python.org/packages/2.6/s/setuptools/setuptools-0.6c11-py2.6.egg)
Processing setuptools-0.6c11-py2.6.egg
Copying setuptools-0.6c11-py2.6.egg to /usr/local/lib/python2.6/dist-packages
Adding setuptools 0.6c11 to easy-install.pth file
Installing easy_install script to /usr/local/bin
Installing easy_install-2.6 script to /usr/local/bin

Installed /usr/local/lib/python2.6/dist-packages/setuptools-0.6c11-py2.6.egg
Processing dependencies for setuptools==0.6c11
Finished processing dependencies for setuptools==0.6c11

```

Then I removed ez_setup.py

```
rm ez_setup.py
```

After that I runned;
```
sudo python -m easy_install Trac
```

wich gave me :
```

sudo python -m easy_install Trac
Searching for Trac
Best match: Trac 0.11.6
Adding Trac 0.11.6 to easy-install.pth file
Installing trac-admin script to /usr/local/bin
Installing tracd script to /usr/local/bin

Using /home/mhg/Desktop/Trac-0.11.6
Processing dependencies for Trac
Searching for Genshi>=0.5
Reading [http://pypi.python.org/simple/Genshi/](http://pypi.python.org/simple/Genshi/)
Reading [http://genshi.edgewall.org/](http://genshi.edgewall.org/)
Reading [http://genshi.edgewall.org/wiki/Download](http://genshi.edgewall.org/wiki/Download)
Best match: Genshi 0.5.1
Downloading [http://ftp.edgewall.com/pub/genshi/Genshi-0.5.1.zip](http://ftp.edgewall.com/pub/genshi/Genshi-0.5.1.zip)
Processing Genshi-0.5.1.zip
Running Genshi-0.5.1/setup.py -q bdist_egg --dist-dir /tmp/easy_install-tlpCGI/Genshi-0.5.1/egg-dist-tmp-BGRPYd
warning: no previously-included files found matching 'doc/2000ft.graffle'
warning: no previously-included files matching '*' found under directory 'doc/logo.lineform'
genshi/_speedups.c:14:20: error: Python.h: No such file or directory
genshi/_speedups.c:15:26: error: structmember.h: No such file or directory
genshi/_speedups.c:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c: In function &#8216;init_constants&#8217;:
genshi/_speedups.c:29: error: &#8216;PyObject&#8217; undeclared (first use in this function)
genshi/_speedups.c:29: error: (Each undeclared identifier is reported only once
genshi/_speedups.c:29: error: for each function it appears in.)
genshi/_speedups.c:29: error: &#8216;util&#8217; undeclared (first use in this function)
genshi/_speedups.c:29: warning: implicit declaration of function &#8216;PyImport_ImportModule&#8217;
genshi/_speedups.c:30: error: &#8216;stripentities&#8217; undeclared (first use in this function)
genshi/_speedups.c:30: warning: implicit declaration of function &#8216;PyObject_GetAttrString&#8217;
genshi/_speedups.c:31: error: &#8216;striptags&#8217; undeclared (first use in this function)
genshi/_speedups.c:32: warning: implicit declaration of function &#8216;Py_DECREF&#8217;
genshi/_speedups.c:34: error: &#8216;amp1&#8217; undeclared (first use in this function)
genshi/_speedups.c:34: warning: implicit declaration of function &#8216;PyUnicode_DecodeASCII&#8217;
genshi/_speedups.c:34: error: &#8216;NULL&#8217; undeclared (first use in this function)
genshi/_speedups.c:35: error: &#8216;amp2&#8217; undeclared (first use in this function)
genshi/_speedups.c:36: error: &#8216;lt1&#8217; undeclared (first use in this function)
genshi/_speedups.c:37: error: &#8216;lt2&#8217; undeclared (first use in this function)
genshi/_speedups.c:38: error: &#8216;gt1&#8217; undeclared (first use in this function)
genshi/_speedups.c:39: error: &#8216;gt2&#8217; undeclared (first use in this function)
genshi/_speedups.c:40: error: &#8216;qt1&#8217; undeclared (first use in this function)
genshi/_speedups.c:41: error: &#8216;qt2&#8217; undeclared (first use in this function)
genshi/_speedups.c: At top level:
genshi/_speedups.c:46: warning: return type defaults to &#8216;int&#8217;
genshi/_speedups.c:46: warning: function declaration isn&#8217;t a prototype
genshi/_speedups.c: In function &#8216;PyAPI_DATA&#8217;:
genshi/_speedups.c:46: error: expected declaration specifiers before &#8216;MarkupType&#8217;
genshi/_speedups.c:48: error: expected declaration specifiers before &#8216;PyDoc_STRVAR&#8217;
genshi/_speedups.c:52: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:165: error: expected declaration specifiers before &#8216;PyDoc_STRVAR&#8217;
genshi/_speedups.c:186: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:206: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:213: error: expected declaration specifiers before &#8216;PyDoc_STRVAR&#8217;
genshi/_speedups.c:229: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:280: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:309: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:385: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:414: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:439: error: expected declaration specifiers before &#8216;PyDoc_STRVAR&#8217;
genshi/_speedups.c:450: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:468: error: expected declaration specifiers before &#8216;PyDoc_STRVAR&#8217;
genshi/_speedups.c:481: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:506: error: expected declaration specifiers before &#8216;PyDoc_STRVAR&#8217;
genshi/_speedups.c:514: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
genshi/_speedups.c:534: error: expected specifier-qualifier-list before &#8216;PyUnicodeObject&#8217;
genshi/_speedups.c:535: error: storage class specified for parameter &#8216;MarkupObject&#8217;
genshi/_speedups.c:537: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Markup_methods&#8217;
genshi/_speedups.c:548: error: expected declaration specifiers before &#8216;;&#8217; token
genshi/_speedups.c:550: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Markup_as_number&#8217;
genshi/_speedups.c:556: error: expected declaration specifiers before &#8216;;&#8217; token
genshi/_speedups.c:558: error: expected declaration specifiers before &#8216;PyTypeObject&#8217;
genshi/_speedups.c:615: error: expected declaration specifiers before &#8216;;&#8217; token
genshi/_speedups.c:617: error: expected declaration specifiers before &#8216;PyMODINIT_FUNC&#8217;
genshi/_speedups.c:535: error: declaration for parameter &#8216;MarkupObject&#8217; but no such parameter
genshi/_speedups.c:634: error: expected &#8216;{&#8217; at end of input
**********************************************************************
WARNING:
An optional C extension could not be compiled, speedups will not be
available.
**********************************************************************
Adding Genshi 0.5.1 to easy-install.pth file

Installed /usr/local/lib/python2.6/dist-packages/Genshi-0.5.1-py2.6-linux-i686.egg
Finished processing dependencies for Trac

```

I did not like the errors but did after doing ```
sudo python -m easy_install Trac
```
again it only said; 
```
Searching for Trac
Best match: Trac 0.11.6
Trac 0.11.6 is already the active version in easy-install.pth
Installing trac-admin script to /usr/local/bin
Installing tracd script to /usr/local/bin

```


In a terminal when I type tra and press TAB twice I now have trac-admin and tracd


Although I have no Idea what to actually do with it it i can run ```
trac-admin
``` 

wich has the following options:

```
trac-admin - The Trac Administration Console 0.11.6

Usage: trac-admin </path/to/projenv> [command [subcommand] [option ...]]

Invoking trac-admin without command starts interactive mode.
help
	-- Show documentation

initenv
	-- Create and initialize a new environment interactively

initenv <projectname> <db> <repostype> <repospath>
	-- Create and initialize a new environment from arguments

hotcopy <backupdir>
	-- Make a hot backup copy of an environment

resync
	-- Re-synchronize trac with the repository

resync <rev>
	-- Re-synchronize only the given <rev>

upgrade
	-- Upgrade database to current version

deploy <directory>
	-- Extract static resources from Trac and all plugins.

permission list [user]
	-- List permission rules

permission add <user> <action> [action] [...]
	-- Add a new permission rule

permission remove <user> <action> [action] [...]
	-- Remove permission rule

wiki list
	-- List wiki pages

wiki remove <page>
	-- Remove wiki page

wiki export <page> [file]
	-- Export wiki page to file or stdout

wiki import <page> [file]
	-- Import wiki page from file or stdin

wiki dump <directory>
	-- Export all wiki pages to files named by title

wiki load <directory>
	-- Import all wiki pages from directory

wiki upgrade
	-- Upgrade default wiki pages to current version

ticket remove <number>
	-- Remove ticket

ticket_type list
	-- Show possible ticket types

ticket_type add <value>
	-- Add a ticket type

ticket_type change <value> <newvalue>
	-- Change a ticket type

ticket_type remove <value>
	-- Remove a ticket type

ticket_type order <value> up|down
	-- Move a ticket type up or down in the list

priority list
	-- Show possible ticket priorities

priority add <value>
	-- Add a priority value option

priority change <value> <newvalue>
	-- Change a priority value

priority remove <value>
	-- Remove priority value

priority order <value> up|down
	-- Move a priority value up or down in the list

severity list
	-- Show possible ticket severities

severity add <value>
	-- Add a severity value option

severity change <value> <newvalue>
	-- Change a severity value

severity remove <value>
	-- Remove severity value

severity order <value> up|down
	-- Move a severity value up or down in the list

component list
	-- Show available components

component add <name> <owner>
	-- Add a new component

component rename <name> <newname>
	-- Rename a component

component remove <name>
	-- Remove/uninstall component

component chown <name> <owner>
	-- Change component ownership

version list
	-- Show versions

version add <name> [time]
	-- Add version

version rename <name> <newname>
	-- Rename version

version time <name> <time>
	-- Set version date (Format: "YYYY-MM-DD", "now" or "")

version remove <name>
	-- Remove version

milestone list
	-- Show milestones

milestone add <name> [due]
	-- Add milestone

milestone rename <name> <newname>
	-- Rename milestone

milestone due <name> <due>
	-- Set milestone due date (Format: "YYYY-MM-DD", "now" or "")

milestone completed <name> <completed>
	-- Set milestone completed date (Format: "YYYY-MM-DD", "now" or "")

milestone remove <name>
	-- Remove milestone

resolution list
	-- Show possible ticket resolutions

resolution add <value>
	-- Add a resolution value option

resolution change <value> <newvalue>
	-- Change a resolution value

resolution remove <value>
	-- Remove resolution value

resolution order <value> up|down
	-- Move a resolution value up or down in the list

```

Long story short; 

[b]I did not encounter a zlib error on ubuntu 9.04
using Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
setuptools.__version__
'0.6c11'
[/b]

---

### Post by placrsaeed on 2010-01-29
Hi Mhgsys,

After typing ```
import zlib
``` Python tells me the module is not installed;

```
>>> import zlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named zlib

```It seems that obvious thing to do now is install the zlib module for Python. However I searched through Google but couldn't find anything. The Zlib ([http://www.zlib.net/](http://www.zlib.net/)) website also seems down, any ideas on how to install the zlib module for Python would point me in the right direction.

Many Thanks,

Saeed

---

### Post by mhgsys on 2010-01-29
try installing python-dev 

```
sudo apt-get install python-dev
```

If that doesn't fix it./

Have a look here; 


[http://www.r3idcardwell.com/ubuntu-9-10-karmic-koala-abort-pclzip-lib-php-missing-zlib-extensions-error/](http://www.r3idcardwell.com/ubuntu-9-10-karmic-koala-abort-pclzip-lib-php-missing-zlib-extensions-error/)

in case link go's down. 

   ```
gksudo gedit /etc/apt/sources.list
```

(In the link they want you to use vim, I love vim myself... but perhaps it's easier for you to use gedit)

Once you&#8217;ve opened the file, add the following two lines: *note: Since this post is from nov 09 I guess you should just remove the # in front of the proper lines in your sources.list*

```
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
```
    ```
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
```

After that run ```
sudo apt-get update
```

---

### Post by placrsaeed on 2010-01-29
I'm not sure exactly how I resolved it but I finally managed to install Trac without any errors. I just followed the instructions again provided on the Trac website ([http://trac.edgewall.org/wiki/TracInstall](http://trac.edgewall.org/wiki/TracInstall)). I followed the easy install method.

Thanks for your time and help.

---

### Post by mhgsys on 2010-01-29
Your Welcome,. 

Good to know it's working... I was just about to run live cd of karmic so I could help you better.



You did a update perhaps ?
and did you get to apt-get python-dev?

I want to have the solution for this.. haha, . Not that I need it, but I'd like to know what fixed the problem.,
Perhaps I will be running karmic after all,.. so I can try to get passed the zlib error knowing what fixed it.

---

### Post by placrsaeed on 2010-01-29
I think you're right. I do actually remember doing an update on Thursday which took aaages. That must've been it.

Once again Thanks for your time and help.

The world needs more people like you!

---

### Post by mhgsys on 2010-01-29
No thanks needed'

Glad I could be a help/support for you. 


Great to know it's working now, 

Please mark this thread as solved 
(it's under thread tools)

edit;
thnx

---

