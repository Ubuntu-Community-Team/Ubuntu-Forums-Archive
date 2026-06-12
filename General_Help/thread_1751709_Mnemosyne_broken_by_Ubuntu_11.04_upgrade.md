---
title: "Mnemosyne broken by Ubuntu 11.04 upgrade"
date: 2011-05-07
forum: General Help
---

### Post by genjuroSE on 2011-05-07
Hello!

I recently upgraded to Ubuntu 11.04 and my program call "mnemosyne" broke!
Here is the error:


emil@linux-desk:~$ mnemosyne 
Traceback (most recent call last):
  File "/usr/local/bin/mnemosyne", line 5, in <module>
    pkg_resources.run_script('Mnemosyne==1.2.2', 'mnemosyne')
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 467, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1194, in run_script
    raise ResolutionError("No script named %r" % script_name)
pkg_resources.ResolutionError: No script named 'mnemosyne'



If someone knows how to fix this, then please let me know. Would be super appreciated!!

Best,
Emil

---

### Post by mtangoo on 2011-05-07
> sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get upgrade --fix-broken
and try again!

---

### Post by genjuroSE on 2011-05-07
mtangoo, thanks a lot for the input (and quick response). 
But executing mnemosyne still gives me the same errors.

---

### Post by genjuroSE on 2011-05-07
I found a possible solution at:

[http://groups.google.com/group/mnemosyne-proj-users/browse_thread/thread/6dac8f2febf308b1](http://groups.google.com/group/mnemosyne-proj-users/browse_thread/thread/6dac8f2febf308b1)

So it could be the version of python-sip that is the problem. Does anyone know how to downgrade? I have tried:

$ sudo apt-get install python-sip=4.10.5-0ubuntu1

to install the older version, but I have no idea if there are older versions in the repository. Does anyone know how to check for old version-names? 

Or is there another solution? I tried looking for the 4.10 elsewhere, but can not find a download.

---

