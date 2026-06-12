---
title: "cannot remove bad installation of autokey"
date: 2009-09-19
forum: General Help
---

### Post by afbase on 2009-09-19
I need help removing [autokey]("http://autokey.sourceforge.net/").  I had downloaded the source file.  I tried installing it but dpkg failed to build the code.  It required python2.6

I installed python2.6 and tried it again.  dpkg couldn't find python2.6 even though /usr/lib/python2.6 existed.  Anyways,  I realized later on that I could just use the Launchpad PPA for autokey found [here]("https://launchpad.net/%7Ecdekter/+archive/ppa").  

So this is my problem:
```

$ sudo apt-get install autokey
Reading package lists...
Building dependency tree...
Reading state information...
autokey is already the newest version.
The following packages were automatically installed and are no longer required:
  libjna-java libswing-layout-java libfreemarker-java javahelp2
  liblucene2-java jetty libini4j-java libdb-je-java libswingworker-java
  libdb4.5-java-gcj libdb4.5-java libjtidy-java
  libxml-commons-resolver1.1-java libappframework-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/79.7kB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package autokey.
(Reading database ... 215347 files and directories currently installed.)
Preparing to replace autokey 0.60.5-0~intrepid (using .../autokey_0.60.5-0~intrepid_all.deb) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/autokey_0.60.5-0~intrepid_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/autokey_0.60.5-0~intrepid_all.deb

```hmmm not good.  I tried:

```
 
$ sudo apt-get -f purge autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjna-java libswing-layout-java libfreemarker-java javahelp2
  liblucene2-java jetty libini4j-java libdb-je-java libswingworker-java
  libdb4.5-java-gcj libdb4.5-java libjtidy-java
  libxml-commons-resolver1.1-java libappframework-java
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  autokey*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 471kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing autokey (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)

```:confused:

Now i'm not sure what to do to fix my problem.  Any help is appreciated. 

My ultimate goal is to have Autokey installed and working properly so I can write LateX papers faster.   I imagine I need to remove the bad installation and then reinstall it.

Thanks.

---

### Post by marshag63 on 2009-09-19
Try these steps:

sudo apt-get --purge remove autokey
sudo rm -Rf /usr/local/lib/python*/dist-packages/autokey*
sudo rm /usr/local/bin/autokey

***Then install again (don't install it any other way) ADD THE PPA TO SOURCES FOLLOWING BELOW DIRECTIONS
[https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa)

Autokey is a great little program.  :)

MarshaG

---

### Post by afbase on 2009-09-19
It doesn't work very well.
```

$ sudo apt-get --purge remove autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjna-java libswing-layout-java libfreemarker-java javahelp2
  liblucene2-java jetty libini4j-java libdb-je-java libswingworker-java
  libdb4.5-java-gcj libdb4.5-java libjtidy-java
  libxml-commons-resolver1.1-java libappframework-java
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  autokey*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 471kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing autokey (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by marshag63 on 2009-09-19
Did you do the next two commands?  You need to do all three to remove autokey.

MarshaG.

---

### Post by wojox on 2009-09-19
If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands:

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

And then try again. It may be necessary to run the second of the above commands more than once.

---

### Post by afbase on 2009-09-19
:confused: not working  still.
```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjna-java libswing-layout-java libfreemarker-java javahelp2
  liblucene2-java jetty libini4j-java libdb-je-java libswingworker-java
  libdb4.5-java-gcj libdb4.5-java libjtidy-java
  libxml-commons-resolver1.1-java libappframework-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/79.7kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 215347 files and directories currently installed.)
Preparing to replace autokey 0.60.5-0~intrepid (using .../autokey_0.60.5-0~intrepid_all.deb) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/autokey_0.60.5-0~intrepid_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/autokey_0.60.5-0~intrepid_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` and i tried the second one twice
```

$ sudo dpkg --configure -a
dpkg: error processing autokey (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 autokey


$sudo dpkg --configure -a
dpkg: error processing autokey (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 autokey


```

---

### Post by marshag63 on 2009-09-19
I just found this post of someone with same problem - here's how he solved it (he had to use aptitude because apt wouldn't work):


 Re: Package stuck - can't remove
Ok, here's how I got past this issue:

Code:

% sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
% sudo vim /var/lib/dpkg/status

I then remove the section for autokey and save

Code:

sudo dpkg --configure -a
sudo aptitude upgdate
sudo aptitude upgrade

I can now upgrade other packages, which the error prevented me from doing before. I realize that the package files are all still on my machine, but this at least solves some of the puzzle.

---

### Post by afbase on 2009-09-19
> **marshag63 said:**
> I just found this post of someone with same problem - here's how he solved it (he had to use aptitude because apt wouldn't work):


 Re: Package stuck - can't remove
Ok, here's how I got past this issue:

Code:

% sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
% sudo vim /var/lib/dpkg/status

I then remove the section for autokey and save

Code:

sudo dpkg --configure -a
sudo aptitude upgdate
sudo aptitude upgrade

I can now upgrade other packages, which the error prevented me from doing before. I realize that the package files are all still on my machine, but this at least solves some of the puzzle.
I just followed your steps.  I then proceeded with the following.
:confused:

```

$ sudo aptitude install autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  autokey 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/79.7kB of archives. After unpacking 471kB will be used.
Writing extended state information... Done
Selecting previously deselected package autokey.
(Reading database ... 214487 files and directories currently installed.)
Unpacking autokey (from .../autokey_0.60.5-0~intrepid_all.deb) ...
Processing triggers for man-db ...
Setting up autokey (0.60.5-0~intrepid) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error processing autokey (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up autokey (0.60.5-0~intrepid) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error processing autokey (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done



```I'm guessing the autokey debian package for the intrepid build from this Launchpad PPA account is not working.  Shall I try using a different build?

---

### Post by marshag63 on 2009-09-19
after you added the PPA and its GPG key, did you let your computer update its sources? looks like the problem to me.

Try installing through Synaptic once you added PPA and GPG key.

---

### Post by afbase on 2009-09-19
> **marshag63 said:**
> after you added the PPA and its GPG key, did you let your computer update its sources? looks like the problem to me.

Try installing through Synaptic once you added PPA and GPG key.

I'm pretty sure I've done all of this stuff already but i'll do it again.

```

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E3C0CE5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6E3C0CE5
gpg: requesting key 6E3C0CE5 from hkp server keyserver.ubuntu.com
gpg: key 6E3C0CE5: "Launchpad Autokey Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

---

### Post by afbase on 2009-09-20
Installing the intrepid version through synaptic doesn't work.

---

### Post by marshag63 on 2009-09-20
Its probably best you post at the Autokey forum so you can be walked through clean-up and setup.

[http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)

There is also an IRC forum ##autokey on irc.freenode.net, but its still pretty quiet there at this point.

I'm sure you will love it once you get it installed - it can lots of things :)

MarshaG.

---

### Post by afbase on 2009-09-20
> **marshag63 said:**
> Its probably best you post at the Autokey forum so you can be walked through clean-up and setup.

[http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)

There is also an IRC forum ##autokey on irc.freenode.net, but its still pretty quiet there at this point.

I'm sure you will love it once you get it installed - it can lots of things :)

MarshaG.
Oh I'm sure I will love it.  I really don't want to type every character of 18 pages of LateX in one weekend.

---

### Post by afbase on 2009-09-20
```

$ sudo dpkg-buildpackage -us  -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package autokey
dpkg-buildpackage: source version 0.60.5-0~jaunty
dpkg-buildpackage: source changed by Chris Dekter <cdekter@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: python (>= 2.6)
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)

```
I tried the same code again.  The only trouble is "dpkg-checkbuilddeps: Unmet build dependencies: python (>= 2.6)"

I have python2.6 (/usr/lib/python2.6).  How do I tell dpkg that I have python2.6?

---

### Post by marshag63 on 2009-09-20
Perhaps uninstalling autokey and then installing the dependencies as below, before reinstalling autokey might fix it:

Dependencies:
python-xlib python-qt4 python-kde4 python-qscintilla2

(I know it specifically needs these packages).

Hope this helps!  :)

MarshaG.

---

### Post by afbase on 2009-09-20
I have a weird installation of Autokey.
From one suggestion on google Forums found [here]("http://groups.google.com/group/autokey-users/browse_thread/thread/6e2dbe9b714478ad")
I deleted python2.6
```

sudo apt-get purge python2.6

```I then did my best to remove Autokey and then reinstall it.  This is what error I get installing it.
```


$ sudo apt-get install autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autokey
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 79.7kB of archives.
After this operation, 471kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net intrepid/main autokey 0.60.5-0~intrepid [79.7kB]
Fetched 79.7kB in 1s (66.5kB/s) 
Selecting previously deselected package autokey.
(Reading database ... 213896 files and directories currently installed.)
Unpacking autokey (from .../autokey_0.60.5-0~intrepid_all.deb) ...
Processing triggers for man-db ...
Setting up autokey (0.60.5-0~intrepid) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error processing autokey (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It doesn't seem like anything new (unless I'm not reading everything).


I just tried typing ```
autokey --configure
``` in Command Line. and I got a configuration window.  I freaked out with joy and confusion.  I checked my toolbar's Applications > Accessories > Autokey.  Sure enough it was located there and I got an error message from opening it from that toolbar.


I've posted some screenshots.



```
  p, li { white-space: pre-wrap; }  Unable to connect to EvDev daemon:
 (11, 'Resource temporarily unavailable')
 
``` ^^^^^^This is the error^^^^^

---

### Post by afbase on 2009-09-20
> **afbase said:**
> I have a weird installation of Autokey.
From one suggestion on google Forums found [here]("http://groups.google.com/group/autokey-users/browse_thread/thread/6e2dbe9b714478ad")
I deleted python2.6
```

sudo apt-get purge python2.6

```I then did my best to remove Autokey and then reinstall it.  This is what error I get installing it.
```


$ sudo apt-get install autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autokey
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 79.7kB of archives.
After this operation, 471kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net intrepid/main autokey 0.60.5-0~intrepid [79.7kB]
Fetched 79.7kB in 1s (66.5kB/s) 
Selecting previously deselected package autokey.
(Reading database ... 213896 files and directories currently installed.)
Unpacking autokey (from .../autokey_0.60.5-0~intrepid_all.deb) ...
Processing triggers for man-db ...
Setting up autokey (0.60.5-0~intrepid) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error processing autokey (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It doesn't seem like anything new (unless I'm not reading everything).


I just tried typing ```
autokey --configure
``` in Command Line. and I got a configuration window.  I freaked out with joy and confusion.  I checked my toolbar's Applications > Accessories > Autokey.  Sure enough it was located there and I got an error message from opening it from that toolbar.


I've posted some screenshots.



```
  p, li { white-space: pre-wrap; }  Unable to connect to EvDev daemon:
 (11, 'Resource temporarily unavailable')
 
``` ^^^^^^This is the error^^^^^
Well the good news is that I have Autokeys working!  I had to change it from the EvDev Daemon to the XRecord.  It was done by going to Settings > Advanced Configuration > Interface

Choose the XRecord Radio Button.  


The only question remaining is why does aptitude/apt-get see my installation as improperly installed?   I don't want to mark this thread as [solved] just yet.  But I don't think the question will bother me too much

---

### Post by cdekter on 2009-09-21
> **afbase said:**
> Well the good news is that I have Autokeys working!  I had to change it from the EvDev Daemon to the XRecord.  It was done by going to Settings > Advanced Configuration > Interface

Choose the XRecord Radio Button.  


The only question remaining is why does aptitude/apt-get see my installation as improperly installed?   I don't want to mark this thread as [solved] just yet.  But I don't think the question will bother me too much

The errors still indicate that there is a problem with your Python install. Without access to your system, it would be hard to say exactly what the problem is, however. This is the cause of the failed install in apt/Synaptic. Until your resolve this problem, other Python applications may also fail to install correctly or run.

---

### Post by afbase on 2009-09-21
> **cdekter said:**
> The errors still indicate that there is a problem with your Python install. Without access to your system, it would be hard to say exactly what the problem is, however. This is the cause of the failed install in apt/Synaptic. Until your resolve this problem, other Python applications may also fail to install correctly or run.

Well I thought i had removed python2.6 but /usr/lib/python2.6 exists and there are plenty of files in it still: I tried it again

```
$ sudo apt-get purge python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python2.6 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up autokey (0.60.5-0~intrepid) ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 15, in <module>
    from autokey import evdev, daemon
ImportError: No module named autokey
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error processing autokey (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ python2.6
Python 2.6 (r26:66714, Sep 18 2009, 09:00:50) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

This seems really fishy.  Could somebody explain to me how to remove python2.6?

---

