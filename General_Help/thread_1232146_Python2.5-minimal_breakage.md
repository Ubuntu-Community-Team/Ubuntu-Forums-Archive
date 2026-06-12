---
title: "Python2.5-minimal breakage"
date: 2009-08-05
forum: General Help
---

### Post by emax on 2009-08-05
Hi there,

I have a Hardy box that seems to have hit update problems recently.

Whenever I run an apt-get dist-upgrade, I get the following:

```

emaxwell@sagan:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-3.0 firefox-3.0-gnome-support
  firefox-gnome-support gvfs gvfs-backends libbind9-30 libdns35 libgvfscommon0
  libisc35 libisccc30 libisccfg30 liblwres30 libnautilus-extension1
  libnspr4-0d libnss3-0d libnss3-1d linux-image-2.6.24-24-386 nautilus
  nautilus-data python2.4 python2.4-examples python2.4-minimal
  python2.5-examples xulrunner-1.9 xulrunner-1.9-gnome-support
28 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/37.3MB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python2.5-minimal (2.5.2-2ubuntu6) ...
Linking and byte-compiling packages for runtime python2.5...
pycentral: pycentral rtinstall: package python-setuptools: not overwriting local files
pycentral rtinstall: package python-setuptools: not overwriting local files
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried running the following commands to fix this problem, but to no avail:

```
sudo dpkg-reconfigure -phigh -a
```

```
sudo apt-get -f install
```

I can't uninstall either python2.5-minimal or python2.5 due to a stack of dependancies.

The current states of these packages as reported by dpkg are as follows:

```

pU  python2.5
iF  python2.5-minimal

```

Any pointers, much appreciated.

---

### Post by Soul-Sing on 2009-08-05
Difficult one... :(You do have diskspace left to perform this update?
If so trial and error? Fingers crossed?:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
sudo aptitude update
sudo apt-get reinstall python2.5-minimal

---

### Post by emax on 2009-08-05
Thanks for your suggestions, much appreciated.

I've tried them all but am still in the same position unfortunately.

Disk space isn't an issue on this machine.

Any other suggestions bar a re-install?

---

### Post by Soul-Sing on 2009-08-05
"Normally" (was is normal reg. this error) i would suggest to remove (purge) the package, and then reinstall it. But that is not really an option, because with the removal of this package you bump against depend. etc. and you will remove lots of things.

I did a google search, which didn't help me further. Maybe someone else?

---

### Post by emax on 2009-08-06
Bump!  Anyone?

---

### Post by LinuxJunky on 2009-08-12
Hi emax,

I found a solution in a blog post. See: "[Problem bei Update von Python 2.5 unter Ubuntu 8.04 LTS]("http://blog.dinotools.de/2009/08/12/problem-bei-update-von-python-2-5-unter-ubuntu-8-04-lts")" (german)

Try the following:

First remove python2.5-minimal and use the --force-depends option.

```
sudo dpkg -r --force-depends python2.5-minimal
```

Fix all dependencies with:

```
sudo apt-get -f install
```

Regards LinuxJunky

---

### Post by emax on 2009-08-12
> **LinuxJunky said:**
> Hi emax,

I found a solution in a blog post. See: "[Problem bei Update von Python 2.5 unter Ubuntu 8.04 LTS]("http://blog.dinotools.de/2009/08/12/problem-bei-update-von-python-2-5-unter-ubuntu-8-04-lts")" (german)

Try the following:

First remove python2.5-minimal and use the --force-depends option.

```
sudo dpkg -r --force-depends python2.5-minimal
```

Fix all dependencies with:

```
sudo apt-get -f install
```

Regards LinuxJunky

Thanks LinuxJunky that did the trick!  I have to admit, I did feel a tad nervous running the first command ;-)

---

### Post by Soul-Sing on 2009-08-12
LinuxJunky thx.

---

### Post by Ingenium on 2009-09-18
I force removed python2.5-minimal and then reinstalled it as stated, but I'm still getting the error. This is a fresh install...

I get the following error: ConfigParser.NoSectionError: No section: 'pycentral'

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python2.5-minimal
The following NEW packages will be installed:
  python2.5-minimal
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1272kB of archives.
After this operation, 4784kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package python2.5-minimal.
(Reading database ... 143421 files and directories currently installed.)
Unpacking python2.5-minimal (from .../python2.5-minimal_2.5.4-1ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Setting up python2.5-minimal (2.5.4-1ubuntu4) ...
Linking and byte-compiling packages for runtime python2.5...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1740, in run
    pkg = DebPackage('package', pkgname, oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

