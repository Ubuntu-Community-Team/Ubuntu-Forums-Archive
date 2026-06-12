---
title: "Ubuntu 9.10 - Error importing python modules - $PYTHONPATH?"
date: 2009-12-04
forum: General Help
---

### Post by knny on 2009-12-04
Hello Forum,

I have been recently encountering problems when, trying to run *ANY* Python program. I get an import error and a warning to verify my PYTHONPATH.
This happened when I removed python-sphinx with apt-get, but I think it's not the reason.

Sample:
$ hg

OUTPUT:
[I]abort: couldn't find mercurial libraries in [/usr/bin /usr/local/lib/python2.6/dist-packages/vipy-0.4-py2.6.egg /usr/local/lib/python2.6/dist-packages/nose-0.11.1-py2.6.egg /usr/local/lib/python2.6/dist-packages/rope-0.9.2-py2.6.egg /usr/local/lib/python2.6/dist-packages/Sphinx-0.6.3-py2.6.egg /usr/local/lib/python2.6/dist-packages/django_html-0.0.1-py2.6.egg /usr/local/lib/python2.6/dist-packages/html5lib-0.11.1-py2.6.egg /home/kenny/Projects/soclone-read-only /home/kenny/python/Django /home/kenny/python/pysmell /home/kenny/python/Django/ropemode /home/kenny/python/Django/rope /home/kenny/python/lib /usr/lib/pymodules/python2.6/mercurial /usr/lib/python2.6 /usr/lib/python2.6/plat-linux2 /usr/lib/python2.6/lib-tk /usr/lib/python2.6/lib-old /usr/lib/python2.6/lib-dynload /usr/local/lib/python2.6/dist-packages]
(check your install and PYTHONPATH)
[/I]
I could just go on like this..
The only Python program actually executing is the Python Interpreter itself, but also importing program-specific libraries doesn't work; only essential modules like sys, os are available.

The sys.path corresponds to the upper listing.

[SIZE="5"]Is there any way to correct this issue?[/SIZE]

---

### Post by Jim_in_Germany on 2009-12-04
Hi,

From this website: [http://mercurial.selenic.com/wiki/UnixInstall]("http://mercurial.selenic.com/wiki/UnixInstall")

> If PYTHONPATH is not correctly set, then hg debuginstall will print an error message that says "abort: couldn't find mercurial libraries in [...](check your install and PYTHONPATH)"

Answer is presumably to set PYTHONPATH.
A quick search of the forums produces this link: [http://ubuntuforums.org/showthread.php?t=520835]("http://ubuntuforums.org/showthread.php?t=520835")

Don't use Python personally (more of a Ruby fan), but I hope that helps nonetheless.

---

