---
title: "Sudden death of a ubuntu 9.10 system"
date: 2010-04-30
forum: General Help
---

### Post by extracrispy on 2010-04-30
Hi, I've been running Ubuntu for about 8 months as my main system dual booting with Windows Vista. A few days ago I was suddenly kicked out of X into a terminal and informed that hundreds of packages were to be uninstalled. I had noticed in the package manager that I had both python 2.5 and 3.6 installed and wanted to remove them both so I could re-install python to fix errors I was getting with py-dev and eclipse. Am I making sense so far? Anyway, my previously fine ubuntu install is steadfastly refusing to boot into anything other than a shell, no X, no networking and running aptitude it shows it wants to install over a thousand packages. 

Thats what happened. I've scoured google and found loads of helpful suggestions but none of them work. I'm hoping to connect to the the internet and let the packages install but nothing I do has any effect. I got a little desperate today and tried to install the latest ubuntu but that went wrong with a media error. Incidentally, the install listed my 9.10 installation as one of the pre-existing operating systems but failed to allow me to import my users from the 9.10 install. My users are all in a separate partition so hopefully the data is safe.

My current hope is that I can use a livecd session to download the necessary packages or tweak the broken 9.10 into working again.

I'm now quite lost and would appreciate any help you can give.

cheers

---

### Post by tgalati4 on 2010-04-30
Well, a lot of configuration file gui's are written in python 2.5.  If you deleted it (because is was causing conflicts with your development 3.6 work), then yes breakage would certainly occur.

Back up your important data using a Live Cd and a flash drive or external USB disk.  Then reinstall.  Unless you kept a list of what was uninstalled with the python 2.5 removal, it's hard to get back to your original state.  Reinstall would be simpler at this point.

---

### Post by extracrispy on 2010-05-02
Thanks tgalati4, I've pretty much got to that point, helped by having to use Vista for a couple of days! My main concern was to restore the user accounts after the clean install but I've just realized that once I create the users then I can re-direct them to use the old folders. I will definitely remember to leave python 2.5 well alone in future and to actually look at the list of additional packages that will be removed. 

All knowledge has a price eh?

---

### Post by tgalati4 on 2010-05-02
Some developers use a Virtual Machine to install their development evironment because they don't want to break their primary installation.

I'm pretty sure that python 2.5 and 3.X can live happily side-by-side, but you need to create links and set up your development environment to use the desired version.

tgalati4@tpad-Gloria7 ~ $ which python
/usr/bin/python

tgalati4@tpad-Gloria7 /usr/bin $ ls -la py*
-rwxr-xr-x 1 root root    3751 2009-04-16 20:57 py3_compilefiles
-rwxr-xr-x 1 root root   90048 2009-04-16 20:57 pycentral
-rwxr-xr-x 1 root root    3723 2009-04-16 20:57 py_compilefiles
lrwxrwxrwx 1 root root       8 2009-07-25 15:45 pydoc -> pydoc2.6
-rwxr-xr-x 1 root root      79 2010-01-20 15:05 pydoc2.5
-rwxr-xr-x 1 root root      79 2009-04-18 19:44 pydoc2.6
lrwxrwxrwx 1 root root      12 2009-07-25 15:45 pygettext -> pygettext2.6
-rwxr-xr-x 1 root root   22103 2010-01-20 15:05 pygettext2.5
-rwxr-xr-x 1 root root   22103 2009-04-18 19:44 pygettext2.6
-rwxr-xr-x 1 root root    4902 2009-04-09 18:33 pysupport-movemodules
-rwxr-xr-x 1 root root    2441 2006-11-23 13:26 pysupport-parseversions
lrwxrwxrwx 1 root root       9 2009-07-25 15:45 python -> python2.6
-rwxr-xr-x 1 root root 1177204 2010-01-20 15:07 python2.5
-rwxr-xr-x 1 root root 2268568 2009-04-18 19:53 python2.6
lrwxrwxrwx 1 root root      29 2009-07-25 15:45 pyversions -> ../share/python/pyversions.py

I've got 2.5 and 2.6 installed but "python" points to 2.6.  I'm sure 2.5 is the base version for Jaunty (which is what is on this machine) but 2.6 was needed by something that I installed.  I'm pretty sure 2.6 can interpret 2.5 code without issue.

I'm not sure about 3.5 interpretting 2.5 without error.  I was under the impression that some refactoring of 2.5 code is needed to get it to work properly.

Vista is like wearing a wet pair of jeans.  You can appear in public, but you got to change them right away.

---

