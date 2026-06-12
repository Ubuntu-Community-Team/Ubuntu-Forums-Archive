---
title: "So How Did I Break Python...?"
date: 2011-07-21
forum: General Help
---

### Post by Myoldmopar on 2011-07-21
...and more importantly of course, how do I repair it?

Very brief background:
  HP Pavilion, Natty 64-bit
  Everything worked great until yesterday

Current situation:
  A number of apps stopped functioning yesterday, giving this output on the console:
```

Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site

```
  Apparently my $PATH is affected, or if python is used in parsing the $PATH then it is the culprit still, because I can't even run some commands that should be on my $PATH, yet if I traverse to the bin directories I can run those apps fine.  (ls and others still work oddly enough...)

Storyline:
  Unity-launched the applications folder to run an app, and it popped up a recommended download of ConvertAll (simple unit conversion software), which seemed nice, so I got it using the Software Center...no big deal.  It never seemed to function, although it did make it to my unity launcher, so I tried opening from terminal and got the above PYTHON messages.  I decided to punt on the program and uninstall, which I did using sudo apt-get remove convertall, and it got most of the way, then popped up the above message.

  convertall is stuck in the apt-get remove queue, so I have had trouble installing any other software because apt-get always gets stuck there.  

  I read online numerous people have had similar problems, and have fixed it by reinstalling python.  So I went to python's site, and (clever me) thought I'd download the latest version.  Downloaded 3.2, .configure, make, and sudo make install later...nothing changed.  After a lot of continued searching, I thought well, I'll go back and download a version 2 python and do the same thing...completed...unsuccessful.

  As the message states, it can't seem to find module site.  Yet if I open a terminal, and run python, it opens fine.  If I import site, it is successful, and gives the following info:
```
>>> site
<module 'site' from '/usr/local/lib/python2.7/site.pyc'>

```

  So, my knowledge is apparently lacking in the way python needs to interact with PATH variables, etc.  Also, I'd like to remove any unnecessary versions of python, but I don't want to just delete the directories, is there a fluid way of doing that?

  Thanks for any guidance, luckily my system is functioning fine right now as long as I don't need to download anything new with apt-get.  I'm happy to share my $PATH, .bashrc, env, or whatever, just let me know what would help.

Thanks!

---

### Post by Myoldmopar on 2011-07-21
After browsing a bit more I discovered the apt history log, so I looked in there and found the time when things started going bad.  Here is a snip of that file:

```

Start-Date: 2011-07-20  12:32:58
Install: convertall:amd64 (0.4.2-1), libqt4-test:amd64 (4.7.2-0ubuntu6.2, automatic), libqt4-help:amd64 (4.7.2-0ubuntu6.2, automatic), python-qt4:amd64 (4.8.3-2, automatic), python-sip:amd64 (4.12.1-1, automatic), libqtassistantclient4:amd64 (4.6.3-3, automatic), libqt4-scripttools:amd64 (4.7.2-0ubuntu6.2, automatic)
End-Date: 2011-07-20  12:33:36

Start-Date: 2011-07-20  12:34:38
Commandline: apt-get autoremove
Remove: tumbler:amd64 (0.1.21-0ubuntu1), libtumbler-1-0:amd64 (0.1.21-0ubuntu1), libxfce4ui-1-0:amd64 (4.8.0-1), libexo-common:amd64 (0.6.0-1), xfce-keyboard-shortcuts:amd64 (4.8.0-1), tumbler-common:amd64 (0.1.21-0ubuntu1), libgarcon-common:amd64 (0.1.6-0ubuntu2), libthunarx-2-0:amd64 (1.2.1-3ubuntu2), thunar-data:amd64 (1.2.1-3ubuntu2), libgarcon-1-0:amd64 (0.1.6-0ubuntu2), libexo-1-0:amd64 (0.6.0-1)
End-Date: 2011-07-20  12:34:57

Start-Date: 2011-07-20  13:56:24
Commandline: apt-get remove convertall
Remove: convertall:amd64 (0.4.2-1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2011-07-20  13:56:27

Start-Date: 2011-07-20  14:01:21
Commandline: apt-get install python
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2011-07-20  14:01:22

Start-Date: 2011-07-20  14:09:23
Commandline: apt-get remove convertall
Remove: convertall:amd64 (0.4.2-1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2011-07-20  14:09:31

Start-Date: 2011-07-20  14:22:02
Commandline: apt-get remove convertall
Remove: convertall:amd64 (0.4.2-1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2011-07-20  14:22:03

```

I did the autoremove in there because apt-get had been telling me for a while that there were packages I didn't need, and that I should run autoremove.  Hope this helps a little.

Thanks again.

---

### Post by oldfred on 2011-07-21
Big parts of Ubuntu require the standard version of python. You can install the newer python but that is in addition to having the current version.

I would try this ( I normally suggest with a chroot, but if you can get to a command line you need sudo -i (eye not l el or 1 one) or sudo on every line:

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
#then reinstall python
apt-get install --reinstall python

---

### Post by Myoldmopar on 2011-07-21
Thanks for the tips.  I ran the commands under sudo and everything went fine up to the upgrade point.  I updated my kernel a week or so ago when Update Manager requested, so that was up to date, but it did list four packages to upgrade, including python-foolscap, so I said yes to update.

You will notice that in addition to the four that want to be upgraded, I still show 8 that are stuck.  One of these is the convertall that I mentioned in the original post.

```
edwin@RedShift:~$ sudo apt-get upgrade
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gstreamer0.10-tools libgstreamer0.10-0 logrotate python-foolscap
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
```

When I tell it to do this operation, it fetches all four packages fine, but I again receive the same error as I did before:
```
Preparing to replace python-foolscap 0.6.1-1 (using .../python-foolscap_0.6.1-1ubuntu0.1_all.deb) ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error processing /var/cache/apt/archives/python-foolscap_0.6.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-foolscap_0.6.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The thing I don't seem to understand is whether apt is actually *using* python, and can't run python successfully, or if the uninstallation of convertall (or some other app) is _using_ python, which causes an error, which causes apt to stop.

Thanks for the reply!

---

### Post by oldfred on 2011-07-21
Did you also try reinstalling python or does that require python??

I have never set a 
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>].

---

### Post by Myoldmopar on 2011-07-22
Thanks for the reply.  I did try reinstalling python using apt-get as found in the last line of your original instructions:
```
apt-get install --reinstall python
```

It does fail, however, with the same errors.  The output is shown below.  Note that as I am doing these updates and upgrades, the list of "not fully installed or removed" is continuing to grow, because the installations continue to fail.  Should I be concerned about this number moving forward?  
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
16 not fully installed or removed.
Need to get 163 kB/560 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main python all 2.7.1-0ubuntu5 [163 kB]
Fetched 163 kB in 0s (170 kB/s)  
(Reading database ... 298600 files and directories currently installed.)
Preparing to replace python-foolscap 0.6.1-1 (using .../python-foolscap_0.6.1-1_all.deb) ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error processing /var/cache/apt/archives/python-foolscap_0.6.1-1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python 2.7.1-0ubuntu5 (using .../python_2.7.1-0ubuntu5_all.deb) ...
Unpacking replacement python ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Errors were encountered while processing:
 /var/cache/apt/archives/python-foolscap_0.6.1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now, I could reinstall python from source.  As I mentioned in the OP, I did that with python versions 2.7 and 3.2, to no success in fixing the problem.  After doing some reading, I believe that if you install python from source, it will default to installing in a secondary location (/usr/local).  So I could download 2.5, but I want to make sure I do a "re-install" as opposed to a "second install in a second location".  

Any thoughts?  Thanks!

---

### Post by Myoldmopar on 2011-07-22
An interesting side effect of this is that the nvidia x server settings gui can no longer write to xorg.  I often switch between single and dual monitors, and I have been popping that open, switching configurations, and when applicable, I rewrite xorg so it is the same when I reboot.  However, when all this other stuff broke, that broke too!

---

### Post by oldfred on 2011-07-22
It looks like the python reinstalled and then you got the errors on the foolscap again. Not sure how to force a removal like that beyond the standard housecleaning you have already done.

I do not think an older python will help, but perhaps the foolscap needs a different version. But even if you install that version it will not be the default, you have to specify it on the python line when you run a python program and want a different version, so that is difficult to do to any other program.

Not sure what else to suggest.

---

### Post by Myoldmopar on 2011-07-22
Same problem persists even after the attempted reinstall of python.  

I feel like if I could get Python 2.5 reinstalled (or reconfigured), it would go a long way in resetting whatever the problem was.  As I mentioned, I can surely get the source and install from there, but I think it will put it in a secondary directory, and not override the initial installation.  

Is there a way to reinstall python from source and have it be located and configured the way it is packaged with Natty?  

On a "side" note, does anyone out there know what $PYTHONHOME should be set to?  Is it even used under normal circumstances?  My inclination is that it normally isn't used and it is just a fallback in problem situations.  

Thanks!

---

### Post by oldfred on 2011-07-22
I know about as much as your do and found these:

[http://docs.python.org/using/cmdline.html](http://docs.python.org/using/cmdline.html)
[http://bugs.python.org/issue6060](http://bugs.python.org/issue6060)

---

### Post by Myoldmopar on 2011-07-25
Thanks for the links.  I had seen those during my searches, but they weren't much help.  They were a little more help now after learning and experiencing some stuff over the weekend.  By manually setting PYTHONPATH and PYTHONHOME, I am able to *run* python. Here are some variables.  I am setting the paths in my .bashrc.   

```
echo $PYTHONHOME
/usr/local
echo $PYTHONPATH
/usr/local/lib/python2.7
which python
/usr/bin/python
```

So I can run python and import site, and all is well.  However, my apt-get is still broken.  It seems it is trying to run a different python.  

```
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site

```

As I mentioned previously, I had tried installing 2.7 and 3.2 to maybe override everything and repair the brokenness, but it may be clogging things up.  whereis reports several pythons:

```
python: /usr/bin/python /usr/bin/python2.7 /etc/python /etc/python2.7 /usr/lib/python2.5 /usr/lib/python2.7 /usr/lib/python2.6 /usr/lib64/python2.5 /usr/lib64/python2.7 /usr/lib64/python2.6 /usr/local/bin/python2.7-config /usr/local/bin/python3.2m-config /usr/local/bin/python3.2m /usr/local/bin/python3.2-config /usr/local/lib/python3.2 /usr/local/lib/python2.7 /usr/include/python2.7 /usr/include/python2.6 /usr/share/python /usr/share/man/man1/python.1.gz
```

Anyone out there know how to fully remove the extraneous versions to make sure they aren't the culprit?  If they were gone completely, that would certainly help narrow down the problem.  

This hasn't been a huge hassle, because most of my apps are working, but I cannot install new software using apt-get since it is broken, and is starting to become a problem the more time goes by.

Thanks for any help!

---

### Post by oldfred on 2011-07-25
Have you tried reinstalling foolscap and then totally removing it?

---

### Post by Myoldmopar on 2011-07-26
Well, I messed around a lot last night, and the status is slightly changed.  I am no longer using the PYTHONPATH or PYTHONHOME variables, that was an old feature that I shouldn't have been using anyway...although it did help track down some problems.  To get by, I ended up just pointing the /usr/bin/python symlink to my ?new? install of Python2.7 in /usr/local/bin.  This is not the right solution, but if I point it anywhere else, I pretty much can't do anything.  So the current status is:

apt-get is working fine...all pending installations and removals were completed

when I type an invalid command into bash, I get the following warning:
```
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 10, in <module>
    import CommandNotFound
ImportError: No module named CommandNotFound

```
Which of course means that the instance of python that Ubuntu is using to parse commands can't seem to find the module

my dual-monitor set up is broken...I use nvidia-settings to manage it, and it can't write the xorg file...If I run from terminal I get the following error:
```
Traceback (most recent call last):
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 20, in <module>
    import gtk, gobject, sys, dbus, logging, os, re
ImportError: No module named gtk

```
so again, the version of python running just can't seem to locate libraries

my debugging environment (for Intel Fortran), idbc, isn't fully functional (presumably because of python errors)

update manager and software center can't open (presumably because of python errors)

So if I go into python manually, and try to import some of these libraries, I can work through the dependencies a bit.  I can find the CommandNotFound.py file, and append it to the path:
```
sys.path.append("/usr/share/pyshared")

```

Then it leads me to yet another dependency...gdbm...which I can find and append that to the sys.path.  After adding these two dependencies, python can properly import the CommandNotFound module.

So, I think I am either really close to a working solution...or so far away that things are just mysteriously falling into place.  Either way, I think if I could figure out what my sys.path needs to be, I could set it appropriately and be on my way using this "alternative" python install in /usr/local.

On the other hand, if there was some sort of documentation available for what a solid ubuntu-python installation looked like...including simple directory structure with notes, symlinks, library locations, sys.path and other path variables, that would probably go a long way in helping me restore my system to functional order without waiting until Oneiric and just reinstalling everything...

Thanks for all the help so far!!

Oh, and I'm still not sure how I broke it in the first place...but after all this learning, I'll be much more equipped to handle it in the future.

---

### Post by Myoldmopar on 2011-07-26
I noticed dropbox wasn't working...which is kind of a big deal for me...so I had to try to fix this again.  I went to apt-get and ran apt-get install --reinstall nautilus-dropbox.  It failed because it couldn't find /usr/lib/Python2.7/compileall.py.  Odd...I know that that is in the /usr/local/lib directory. 

The /usr/lib/Python2.7 directory is almost empty, so I decided to live dangerously and rename it to _Python2.7.  Then I copied over the Python2.7 library from /usr/local/lib.  No problems during the copy.  Re-ran apt-get to reinstall dropbox...no complaints at all...install went perfectly...dropbox is running fine.  

Got my hopes up a bit, but found that the other stuff still isn't working.

So, I wonder how I can tell which programs are looking for stuff in /usr/lib/Python2.7.

---

