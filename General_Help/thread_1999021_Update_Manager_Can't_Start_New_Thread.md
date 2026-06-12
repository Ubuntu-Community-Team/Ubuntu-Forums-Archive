---
title: "Update Manager: Can't Start New Thread"
date: 2012-06-07
forum: General Help
---

### Post by ackey on 2012-06-07
Hi Everyone,

I got the following error when trying to run update-manager from the terminal in 11.10:

```
ackey@whobuntu:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 109, in <module>
    app.main(options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1209, in main
    self.check_metarelease()
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1196, in check_metarelease
    self.options.use_proposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/MetaReleaseGObject.py", line 37, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/MetaRelease.py", line 136, in __init__
    thread.start_new_thread(self.download, ())
thread.error: can't start new thread

```

I don't know how to debug this.  Restarting did not help, and I know that update-manager has run relatively recently on this machine.  My only guess: I had an error in a different program regarding threads and I had installed some new libraries to try to fix it.  Perhaps something is conflicting?  Of course I don't remember what I installed now, but it was all official packages through aptitude.

Synaptic still works.  I haven't found any other programs with the same error message.

Cheers,
Nicole

---

### Post by kanikilu on 2012-06-07
To me, that looks like a problem with python, and not necessarily with update-manager. Which would explain why aptitude/synaptic still work.

Since you said you updated libraries from aptitude, but don't remember what, you can list your recently installed packages (from the wiki):

```
zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort
```

To narrow it down to python, you can try something like:

```
$ python
Python 2.7.3 (default, Apr 20 2012, 22:39:59) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import thread
>>> thread.start_new(lambda: None, ())
```

And see if it gives you the same error...

---

### Post by ackey on 2012-06-07
Hi Kanikilu,

Thank you for the prompt and clear reply - I didn't know/remember about the dpkg log.  It does look like python was recently updated.  When I "ls -l /usr/bin/update-manager" I see it was modified on 5-31.

Here are the most recent lines from the dpkg log:

```

2012-05-29 13:58:31 install linux-image-3.0.0-20-generic <none> 3.0.0-20.34
2012-05-29 13:58:42 install linux-headers-3.0.0-20 <none> 3.0.0-20.34
2012-05-29 13:58:50 install linux-headers-3.0.0-20-generic <none> 3.0.0-20.34
2012-05-29 14:05:20 install sqlite3 <none> 3.7.7-2ubuntu2
2012-05-29 14:15:42 install rescuetime <none> 2.6.0.144
2012-05-29 17:34:10 install gccxml <none> 0.9.0+cvs20110723-2
2012-05-29 17:34:12 install libboost1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:21 install libboost-dev <none> 1.46.1.1
2012-05-29 17:34:22 install libboost-date-time1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:23 install libboost-date-time1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:23 install libboost-serialization1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:24 install libboost-date-time-dev <none> 1.46.1.1
2012-05-29 17:34:25 install libboost-filesystem1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:25 install libboost-system1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:26 install libboost-filesystem1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:26 install libboost-system1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:27 install libboost-filesystem-dev <none> 1.46.1.1
2012-05-29 17:34:28 install libboost-test1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:28 install libboost-test1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:29 install libboost-graph1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:29 install libboost-graph-dev <none> 1.46.1.1
2012-05-29 17:34:30 install libboost-graph-parallel1.46-dev <none> 1.46.1-5ubuntu3
2012-05-29 17:34:31 install libboost-graph-parallel-dev <none> 1.46.1.1
2012-05-29 17:34:31 install libboost-regex1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:32 install libicu-dev <none> 4.4.2-2ubuntu0.11.10.1
2012-05-29 17:34:34 install libboost-regex1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:35 install libboost-iostreams1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:35 install libboost-iostreams-dev <none> 1.46.1.1
2012-05-29 17:34:36 install libboost-math1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:36 install libboost-math1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:37 install libboost-math-dev <none> 1.46.1.1
2012-05-29 17:34:38 install libibverbs1 <none> 1.1.3-2ubuntu1
2012-05-29 17:34:38 install libnuma1 <none> 2.0.5-1
2012-05-29 17:34:39 install libtorque2 <none> 2.4.15+dfsg-1
2012-05-29 17:34:40 install libboost-mpi1.46.1 <none> 1.46.1-5ubuntu3
2012-05-29 17:34:40 install libopenmpi1.3 <none> 1.4.3-2.1ubuntu1
2012-05-29 17:34:41 install openmpi-common <none> 1.4.3-2.1ubuntu1
2012-05-29 17:34:42 install libibverbs-dev <none> 1.1.3-2ubuntu1
2012-05-29 17:34:42 install libopenmpi-dev <none> 1.4.3-2.1ubuntu1
2012-05-29 17:34:46 install libboost-mpi1.46-dev <none> 1.46.1-5ubuntu3
2012-05-29 17:34:46 install mpi-default-dev <none> 0.6ubuntu1
2012-05-29 17:34:47 install libboost-mpi-dev <none> 1.46.1.1
2012-05-29 17:34:47 install libboost-mpi-python-dev <none> 1.46.1.1
2012-05-29 17:34:48 install libboost-program-options1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:48 install libboost-program-options1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:49 install libboost-program-options-dev <none> 1.46.1.1
2012-05-29 17:34:50 install libboost-python1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:50 install libssl-dev <none> 1.0.0e-2ubuntu4.6
2012-05-29 17:34:51 install python2.7-dev <none> 2.7.2-5ubuntu1
2012-05-29 17:34:54 install python-dev <none> 2.7.2-7ubuntu2
2012-05-29 17:34:55 install libboost-python1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:56 install libboost-python-dev <none> 1.46.1.1
2012-05-29 17:34:56 install libboost-regex-dev <none> 1.46.1.1
2012-05-29 17:34:57 install libboost-serialization-dev <none> 1.46.1.1
2012-05-29 17:34:58 install libboost-signals1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:59 install libboost-signals1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:59 install libboost-signals-dev <none> 1.46.1.1
2012-05-29 17:35:00 install libboost-system-dev <none> 1.46.1.1
2012-05-29 17:35:00 install libboost-test-dev <none> 1.46.1.1
2012-05-29 17:35:01 install libboost-thread1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:35:02 install libboost-thread1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:35:02 install libboost-thread-dev <none> 1.46.1.1
2012-05-29 17:35:03 install libboost-wave1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:35:04 install libboost-wave1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:35:04 install libboost-wave-dev <none> 1.46.1.1
2012-05-29 17:35:05 install libboost-all-dev <none> 1.46.1.1
2012-05-29 17:35:05 install libboost-graph-parallel1.46.1 <none> 1.46.1-5ubuntu3
2012-05-29 17:35:06 install libboost-graph1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:35:07 install libssl-doc <none> 1.0.0e-2ubuntu4.6
2012-06-07 10:40:45 install com.pandora.desktop.fb9956fd96e03239939108614098ad95535ee674.1 <none> 2.0.6

```

Grepping for python, here are just those:

```

2012-05-17 15:57:53 install python-gobject-2 <none> 2.28.6-6svn1
2012-05-17 16:15:23 install python-pyatspi2 <none> 2.2.1-0ubuntu1
2012-05-17 16:21:39 install python-scour <none> 0.26-1
2012-05-29 17:34:47 install libboost-mpi-python-dev <none> 1.46.1.1
2012-05-29 17:34:50 install libboost-python1.46.1 <none> 1.46.1-5ubuntu2
2012-05-29 17:34:51 install python2.7-dev <none> 2.7.2-5ubuntu1
2012-05-29 17:34:54 install python-dev <none> 2.7.2-7ubuntu2
2012-05-29 17:34:55 install libboost-python1.46-dev <none> 1.46.1-5ubuntu2
2012-05-29 17:34:56 install libboost-python-dev <none> 1.46.1.1

```

I am not very familiar with python, so I don't know if the following output is good or bad:
```

ackey@whobuntu:~$ python
Python 2.7.2+ (default, Oct  4 2011, 20:03:08) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import thread
>>> thread.start_new(lambda: None, ())
-1999352976

```

Part of the reason for all of the installed packages on 5-29 was to fix a libboost thread problem in a piece of 3rd part software.  I installed some libboost libraries that required a bunch of python packages.  Given that the libboost libraries didn't fix the other piece of software, should I start trying to uninstall some of the libraries that I installed on 5-29?

-Nicole

---

### Post by kanikilu on 2012-06-07
Hmm, well, you didn't get the "can't start new thread" error, so now I'm not so sure that it's python. I'm not on 11.10, but it looks like you have the latest python packages.

Have you tried reinstalling update-manager? Anyone else have any suggestions?

---

### Post by ackey on 2012-06-07
Reinstalling update-manager didn't seem to help.  But then I realized I hadn't been trying "sudo update-manager" - that doesn't spit out the error and pulls up update-manager.  I'm pretty sure that non-sudo update-manager used to work (and definitely works on another machine), but I can just remember to use sudo first.

I'd be happier if I understood what was broken, since it might be affecting something else.  But now I can at least call update-manager...

---

### Post by kanikilu on 2012-06-07
Yeah, I'm able to run *update-manager* without sudo/gksu.

From searching around, it seems people see that error when a python script is trying to open too many threads for the OS to handle, or allocate too much memory.

For example: [http://blog.tsunanet.net/2010/10/threaderror-cant-start-new-thread.html](http://blog.tsunanet.net/2010/10/threaderror-cant-start-new-thread.html)

But how to go about debugging or fixing that, to be honest, is over my head, sorry.

---

### Post by ackey on 2012-06-07
Thanks for trying to help (-:

I checked the security file mentioned in that blog post and nothing is listed.

I guess I see a fresh install to 12.04 in my future...

---

