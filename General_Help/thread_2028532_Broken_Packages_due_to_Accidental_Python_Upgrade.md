---
title: "Broken Packages due to Accidental Python Upgrade"
date: 2012-07-18
forum: General Help
---

### Post by drmrgd on 2012-07-18
I need to retain 10.04 on my Ubuntu Server.  In an effort to upgrade some stuff on our server for security reasons, however, our IT support accidentally upgraded Python from 2.6 to 2.7.  When I run the configuration script for a particular package that the server needs to run, it's throwing an error about not being able to download and install the libboost-all-dev package.  Tracing that back I find that the issue is:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libboost-python1.40-dev: Depends: python-dev but it is not going to be installed
                           Depends: python (< 2.7) but 2.7.2-7ubuntu2 is to be installed
E: Broken packages
```

So, it looks like it won't overwrite the new libraries with the old ones that are required (which makes sense, but is not what I need).  Unfortunately, I have no control over the system to the point that I absolutely need Python2.6 to be the main version and I need the old libraries to be the active ones.

I tried to set alternatives for Python and tried to select 2.6 as the default one.  That didn't work.  I'm guessing that just purging 2.7 is going to all out nuke the system (correct me if I'm wrong!), and isn't an option.  

Short of reinstalling the system, which is possible but extremely complicated for reasons I won't get in to, is there a way to do any of the following, or am I completely hosed here?

1. Purge Python2.7 so that v2.6 is the only version on this system?

2. Quarantine Python2.7 and its libraries so that the server sees 2.6 and its libraries as that main ones and therefore gets libboost-all-dev?

3. Some other clever solution that works around this dependency issue?

Thanks in advance for the help!

---

### Post by oldfred on 2012-07-18
It used to be just about impossible to repair if the default python was deleted. Perhaps a chroot & total reinstall.

But now I thought you could just reinstall and that fixed it. Depending on how it was installed you may just be able to repair the python folder. There should be a python folder and separate folders for each version. The default in the python folder is just a link to the version to default to.

Not sure if it is just this or more. Others may know exactly:

run this to see where python is:

whereis python

I think it is this:
/usr/share/python

but it may be this link which needs to be to your current version or both?:
/usr/bin/python

---

### Post by drmrgd on 2012-07-18
> **oldfred said:**
> It used to be just about impossible to repair if the default python was deleted. Perhaps a chroot & total reinstall.

But now I thought you could just reinstall and that fixed it. Depending on how it was installed you may just be able to repair the python folder. There should be a python folder and separate folders for each version. The default in the python folder is just a link to the version to default to.

Not sure if it is just this or more. Others may know exactly:

run this to see where python is:

whereis python

I think it is this:
/usr/share/python

but it may be this link which needs to be to your current version or both?:
/usr/bin/python

You're correct in that both versions reside on the system.  By creating an alternatives entry for Python and choosing Python2.6 as the default, I'm able to have the system launch 2.6 when I just type 'python':

```
ionadmin@PCCPGM:~ $ sudo update-alternatives --config python
There are 2 choices for the alternative python (providing /usr/bin/python).

  Selection    Path                Priority   Status
------------------------------------------------------------
  0            /usr/bin/python2.7   20        auto mode
* 1            /usr/bin/python2.6   10        manual mode
  2            /usr/bin/python2.7   20        manual mode

Press enter to keep the current choice[*], or type selection number: 0
update-alternatives: using /usr/bin/python2.7 to provide /usr/bin/python (python) in auto mode.
ionadmin@PCCPGM:~ $ python --version
Python 2.7.2+
ionadmin@PCCPGM:~ $ sudo update-alternatives --config python
There are 2 choices for the alternative python (providing /usr/bin/python).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python2.7   20        auto mode
  1            /usr/bin/python2.6   10        manual mode
  2            /usr/bin/python2.7   20        manual mode

Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /usr/bin/python2.6 to provide /usr/bin/python (python) in manual mode.
ionadmin@PCCPGM:~ $ python --version
Python 2.6.7
```

The issue is in the libboost-all-dev package, which I can trace like this:

```
sudo apt-get install libboost-all-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libboost-all-dev: Depends: libboost1.40-all-dev but it is not going to be installed
E: Broken packages
[100] ionadmin@PCCPGM:~ $ sudo apt-get install libboost1.40-all-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libboost1.40-all-dev: Depends: libboost-python1.40-dev but it is not going to be installed
E: Broken packages
[100] ionadmin@PCCPGM:~ $ sudo apt-get install libboost-python1.40-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libboost-python1.40-dev: Depends: python-dev but it is not going to be installed
                           Depends: python (< 2.7) but 2.7.2-7ubuntu2 is to be installed
E: Broken packages
```

I could, however, be thinking about this the wrong way.  In either case, I think a reimage from a backup is the only way out at this point, although there are a bunch of really clever people on this forum.  So, maybe there's a different way around it.  If I could get the libboost packages installed, I may be able to get this thing functional again (then again, I have no idea what other dependencies are going to come up!).

---

### Post by oldfred on 2012-07-18
My python-dev says it is just a package to install the current version or for me, python2.7-dev.

If you try python2.6-dev what happens?

---

### Post by drmrgd on 2012-07-18
No dice on that as it looks like even the revision of v2.6 is too new:

```
udo apt-get install python2.6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.6-dev: Depends: python2.6 (= 2.6.5-1ubuntu6) but 2.6.7-4ubuntu1 is to be installed
                 Depends: libpython2.6 (= 2.6.5-1ubuntu6) but 2.6.7-4ubuntu1 is to be installed
E: Broken packages
```

This may get me into hot water deeper (although I don't think I can break what's already broken!), but the tech added the Oneiric repo in order to upgrade Apache (the original thing that got us to this point).  I know that's why I'm running into these dependency issues.  I'm sort of wondering what would happen if I re-add the Oneiric repo, and try upgrading these packages again.  I'm assuming that I'm still going to have a problem with libboost-all-dev in the custom package that I need to be run on this server.  Maybe this is a poor assumption, though...

Be back in a few hours.

---

