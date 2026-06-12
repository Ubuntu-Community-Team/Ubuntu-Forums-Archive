---
title: "Installing Python 2.6 on a system with Python 2.7.3"
date: 2012-05-06
forum: General Help
---

### Post by Senior_Buckethead on 2012-05-06
Can I Install Python 2.6 on a system with 2.7.3, because I have an application that will only run under Python 2.6. Is this possible?
Whenever I install the package with dpkg it says it requires 2.6 and aborts.

---

### Post by PeterP24 on 2012-05-06
I have several python versions installed - it is possible. Of course, the latest way to go is to have python 2.7 installed along a 3.x one.

---

### Post by jerome1232 on 2012-05-06
There is a ppa for 2.6, I don't know if it conflicts with 2.7 or not

[https://launchpad.net/~python-dev/+archive/ppa](https://launchpad.net/~python-dev/+archive/ppa)


You can also get the source here

[http://www.python.org/getit/releases/2.6.6/](http://www.python.org/getit/releases/2.6.6/)

---

### Post by Senior_Buckethead on 2012-05-06
```
W: Failed to fetch http://ppa.launchpad.net/python-dev/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/python-dev/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
glenn@acer:~$ 

```

There is no ppa for precise, only hardy and jaunty. see:
[http://ppa.launchpad.net/python-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/python-dev/ppa/ubuntu/dists/)

So, how can I install python 2.6?

---

### Post by PeterP24 on 2012-05-06
I am surprised that you encountered problems in installation of python 2.6.
Here is a demonstration of three side by side python versions on my laptop (Ubuntu 11.04):
```
pts@hal9000:~$ python2.6
Python 2.6.6 (r266:84292, Mar 25 2011, 19:36:32) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
KeyboardInterrupt
>>> quit
Use quit() or Ctrl-D (i.e. EOF) to exit
>>> quit()
pts@hal9000:~$ python2.7
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> quit()
pts@hal9000:~$ python3.2
Python 3.2 (r32:88445, Dec  8 2011, 15:26:58) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> quit()
pts@hal9000:~$ 

```

I installed them by using Synaptic. Actually if you search for python keyword in Synaptic, the first result is a generic package which will install the 2.7 version. If you go for something more specific, like python2.6 you will find what you are looking for.

---

### Post by jerome1232 on 2012-05-06
If it's not in the ppa, then install from source. I linked it from pythons site.

---

### Post by Senior_Buckethead on 2012-05-06
```
glenn@acer:~/Downloads$ sudo dpkg -i makehuman-nightly-linux-i386.deb
Selecting previously unselected package makehuman-nightly.
(Reading database ... 219716 files and directories currently installed.)
Unpacking makehuman-nightly (from makehuman-nightly-linux-i386.deb) ...
dpkg: dependency problems prevent configuration of makehuman-nightly:
 makehuman-nightly depends on python2.6; however:
  Package python2.6 is not installed.
 makehuman-nightly depends on libpython2.6; however:
  Package libpython2.6 is not installed.
dpkg: error processing makehuman-nightly (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 makehuman-nightly
glenn@acer:~/Downloads$ 

```

something is wrong with my system. When I type:
```

glenn@acer:~/Downloads$ python --version
Python 2.6
glenn@acer:~/Downloads$ 

```

How do I uninstall then reinstall python? Because I think it has got itself confused.

---

### Post by PeterP24 on 2012-05-06
@Senior_Buckethead

Are you sure? In a terminal, write python. Check the output above the python prompt - it usually report the version of python you have installed. If it is 2.6.6 or so, you have managed somehow to replace the default installation (2.7). Like I mentioned in a previous post - I am surprised - I always thought that versions of python can coexist. I still believe it! 

Now, you should check in a terminal to see if, during your tries, you installed some other python versions: try first python2.6, then python2.7 or any other versions you might have worked with. Again - I state that Synaptic might be a better choice to install various python versions - you should really give it a try before trying to install from sources or ppas.

---

### Post by Senior_Buckethead on 2012-05-06
```

glenn@acer:/etc/apt/sources.list.d$ python
Python 2.6 (r26:66714, May  5 2012, 12:14:36) 
[GCC 4.6.3] on linux3
Type "help", "copyright", "credits" or "license" for more information.
>>> ^C
KeyboardInterrupt
>>> quit()
glenn@acer:/etc/apt/sources.list.d$

```

And yet when I try to install makehuman:
```

glenn@acer:~/Downloads$ sudo dpkg -i makehuman-nightly-linux-i386.deb
Selecting previously unselected package makehuman-nightly.
(Reading database ... 221956 files and directories currently installed.)
Unpacking makehuman-nightly (from makehuman-nightly-linux-i386.deb) ...
dpkg: dependency problems prevent configuration of makehuman-nightly:
 makehuman-nightly depends on python2.6; however:
  Package python2.6 is not installed.
 makehuman-nightly depends on libpython2.6; however:
  Package libpython2.6 is not installed.
dpkg: error processing makehuman-nightly (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 makehuman-nightly
glenn@acer:~/Downloads$ 

```

I'll try to see if I can reinstall python using synaptic. Something has got to be broken.

---

### Post by Senior_Buckethead on 2012-05-06
> Start by running the script "./configure", which determines your
system configuration and creates the Makefile.  (It takes a minute or
two -- please be patient!)  You may want to pass options to the
configure script -- see the section below on configuration options and
variables.  When it's done, you are ready to run make.

To build Python, you normally type "make" in the toplevel directory.
If you have changed the configuration, the Makefile may have to be
rebuilt.  In this case you may have to run make again to correctly
build your desired target.  The interpreter executable is built in the
top level directory.
Ok, I have downloaded python 2.6. I have unzipped the file and now have a python2.6 directory.
I have run the configure script. All is good.

What do they mean by 'top level directory'? Where should I put the python installation folder before running make?

---

### Post by jerome1232 on 2012-05-07
They mean in the top level of your python directory


So if you source code is at ~/Desktop/python2.6, you'd cd to ~/Desktop/python2.6 then run make. I keep source code I've installed at ~/src, since you have to keep it around if you want to remove the installed software in a nice clean manner in the future.

---

### Post by agger on 2012-05-09
> **PeterP24 said:**
> I am surprised that you encountered problems in installation of python 2.6.
Here is a demonstration of three side by side python versions on my laptop (Ubuntu 11.04):


Yes, but Python 2.6 has been removed from the repositoried in 12.04 thus it's necessary to install from source e.g. I have to do this too, because I have a virtualenv which is dependent on 2.6.

---

### Post by agger on 2012-05-09
But I'm also having trouble installing. After doing a configure, make complains about missing bits:

```

Failed to find the necessary bits to build these modules:
_bsddb             _curses            _curses_panel   
_hashlib           _sqlite3           _ssl            
_tkinter           bsddb185           bz2             
dbm                dl                 gdbm            
imageop            linuxaudiodev      ossaudiodev     
readline           sunaudiodev        zlib            
To find the necessary bits, look in setup.py in detect_modules() for the module's name.


Failed to build these modules:
crypt              nis       

```

Alas, I'm in a situation where having Python 2.6 would've been very helpful. Instead, I may have to find another way around it.

---

### Post by jerome1232 on 2012-05-09
It seems there's a workaround for building python2.6 [HERE]("http://hg.python.org/cpython/rev/00c6957c7719/") which supposedly works, but I can't get it to go. I have however made progress. Steps I have taken:

First installed python2.7 dev dependencies, as I understand they are very similar for 2.6
```
sudo apt-get build-dep python2.7
```

configure seemed to go well, make ran but failed with an error.
```
Traceback (most recent call last):
  File "./setup.py", line 1886, in <module>
    main()
  File "./setup.py", line 1881, in main
    'Lib/smtpd.py']
  File "/home/jeremy/src/Python-2.6/Lib/distutils/core.py", line 152, in setup
    dist.run_commands()
  File "/home/jeremy/src/Python-2.6/Lib/distutils/dist.py", line 975, in run_commands
    self.run_command(cmd)
  File "/home/jeremy/src/Python-2.6/Lib/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/jeremy/src/Python-2.6/Lib/distutils/command/build.py", line 134, in run
    self.run_command(cmd_name)
  File "/home/jeremy/src/Python-2.6/Lib/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/home/jeremy/src/Python-2.6/Lib/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/jeremy/src/Python-2.6/Lib/distutils/command/build_ext.py", line 343, in run
    self.build_extensions()
  File "./setup.py", line 103, in build_extensions
    missing = self.detect_modules()
  File "./setup.py", line 944, in detect_modules
    sqlite_libdir = [os.path.abspath(os.path.dirname(sqlite_libfile))]
  File "/home/jeremy/src/Python-2.6/Lib/posixpath.py", line 119, in dirname
    i = p.rfind('/') + 1
AttributeError: 'NoneType' object has no attribute 'rfind'
make: *** [sharedmods] Error 1

```

Any thoughts?

---

