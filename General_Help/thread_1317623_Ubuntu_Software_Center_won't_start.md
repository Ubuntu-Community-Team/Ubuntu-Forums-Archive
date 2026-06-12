---
title: "Ubuntu Software Center won't start"
date: 2009-11-06
forum: General Help
---

### Post by Chang An on 2009-11-06
I was in the middle of installing a program with the Software Center and my power went out.  I rebooted and noticed I can't launch the Software Center anymore.

I tried to remove the package in Synaptic and got this error: 

subprocess installed pre-removal script returned error exit status 2

Here is the error I get a lot from the terminal:

Sub-process /usr/bin/dpkg returned an error code (1)

I have already tried these commands and none helped.

sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo rm -f /var/cache/apt/archives/*.deb
sudo apt-get update
sudo apt-get upgrade

Any ideas how to fix this? Thanks

---

### Post by michy99 on 2009-11-06
If you open a terminal and enter```
sudo apt-get update
```what error messages do you get?

---

### Post by Chang An on 2009-11-06
I get no errors when I run that.  Also I noticed the Update Manager will not launch.  Thanks for the quick reply by the way.

---

### Post by Chang An on 2009-11-06
When I tried to launch the software center from the terminal I get this error:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

---

### Post by Chang An on 2009-11-07
It seems this broken package has cause multiple programs not to work.  Movieplayer also will not launch now.

---

### Post by Chang An on 2009-11-07
Bump

---

### Post by xtremesupremacy3 on 2009-11-07
This is annoying error and there is a trick to work it, but this is annoying too.

first type 'sudo apt-get install update', then when the error occurs type 'sudo apt-get -f install' to force the installed files that wouldnt load, then try updating again, keep doing this until only one file is left over, then thats the file that causes your main problem

---

### Post by Chang An on 2009-11-07
I did that a couple times and I still end up with this:

dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing exfalso (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 exfalso
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pguedes on 2009-11-09
I too ave the same problem and I'tried the solution presented But I always get the same (bad result)

Just Solved!!!! I've followed a French Ubuntu Forum:

Just go to Synaptic, and search by python, and mark for reinstalation all the packages that you already have installed.

Worked like a Charm!

---

### Post by Chang An on 2009-11-09
I just reinstalled Ubuntu and that fixed my problem.  I also installed 32 bit instead of 64 bit and that fixed my flash problems.  Also I noticed that 32 bit Gnome Do docky will actually launch on start up more often then it did in 64 bit.  I hope by Lucid native 64 bit flash with be a choice by default and Ill try 64 bit again.

---

### Post by ProntoAnthony on 2010-10-18
I'm on 10.04.1 LTS desktop. Switch from gnome to KDE.

I just noticed a problem where I could not load the Ubuntu Software Center. Followed the instructions above.

Still doesn't work. At one point KPackage reported:

p, li { white-space: pre-wrap; } Error Type: 
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
self.refresh_cache(force)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
format_string(error.message))
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
txt = unicode(text, encoding, errors='replace')


The message has not recurred, however the Software Center still won't load.

when I ran "sudo apt-get update" I received error:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by prinspatrick on 2010-11-03
> **pguedes said:**
> I too ave the same problem and I'tried the solution presented But I always get the same (bad result)

Just Solved!!!! I've followed a French Ubuntu Forum:

Just go to Synaptic, and search by python, and mark for reinstalation all the packages that you already have installed.

Worked like a Charm!

software-center wouldn't start anymore in 10.10 and this trick solved my problem :)

Thanks very much!

---

### Post by Attika on 2011-05-30
so i was trying to run minecraft and i found a tutorial that told me to install the Canonical Partner repository *as the first step* by typing

**# sudo apt-get-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" && sudo apt-get update**

i tried to open up the software center almost immediately afterwards and it wouldn't launch. i didn't notice right away, but i tried another time and when it failed to start up i restarted my computer. now there's a giant red circle with a white dash in the middle, and when i click on it the update manager pops up and says

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)' is the error message I get. 

i've tried the commands listed in OP's post; none worked. Help?

---

### Post by hawthornso23 on 2011-05-30
> **Attika said:**
> so i was trying to run minecraft and i found a tutorial that told me to install the Canonical Partner repository *as the first step* by typing

**# sudo apt-get-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" && sudo apt-get update**

i tried to open up the software center almost immediately afterwards and it wouldn't launch. i didn't notice right away, but i tried another time and when it failed to start up i restarted my computer. now there's a giant red circle with a white dash in the middle, and when i click on it the update manager pops up and says

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)' is the error message I get. 

i've tried the commands listed in OP's post; none worked. Help?

The instructions are for lucid. If you were running some other version of ubuntu then trying to use these instructions could cause this kind of mess. In any case adding that repository was obviously a really bad idea - so you want to get rid of it. Since you have update manager running then click on settings and look in other software for the repository you just added. Remove it and run sudo apt-get update again to reinitialize your package information. 

I'm not really a linux guru - but this is what I'd do to try to back out of the situation you are in. I note that your bug really isn't related to the rest of this very old thread. You should start a new thread.

---

### Post by egarzav on 2013-03-15
> **pguedes said:**
> I too ave the same problem and I'tried the solution presented But I always get the same (bad result)

Just Solved!!!! I've followed a French Ubuntu Forum:

Just go to Synaptic, and search by python, and mark for reinstalation all the packages that you already have installed.

Worked like a Charm!

I had this same problem and THIS was the solution.

---

### Post by wildmanne39 on 2013-03-15
Old thread closed!

---

