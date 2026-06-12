---
title: "update manager"
date: 2010-03-26
forum: General Help
---

### Post by esky64 on 2010-03-26
Today when I click on update manager I get no response I go 
System > Administration > Update Manager and nothing happens 
I'm doing updates at the moment in a terminal screen 
Thanks 
Chris

---

### Post by cong06 on 2010-03-26
What happens when you run "update-manager" in the terminal?

I get no output, but maybe if there's an error it posts something?

---

### Post by esky64 on 2010-03-26
chris@chris-desktop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 53, in <module>
    parser = OptionParser()
  File "/usr/lib/python2.6/optparse.py", line 1198, in __init__
    self.set_usage(usage)
  File "/usr/lib/python2.6/optparse.py", line 1273, in set_usage
    self.usage = _("%prog [options]")
  File "/usr/lib/python2.6/gettext.py", line 581, in gettext
    return dgettext(_current_domain, message)
  File "/usr/lib/python2.6/gettext.py", line 545, in dgettext
    codeset=_localecodesets.get(domain))
  File "/usr/lib/python2.6/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.6/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.6/gettext.py", line 273, in _parse
    magic = unpack('<I', buf[:4])[0]
struct.error: unpack requires a string argument of length 4
chris@chris-desktop:~$

---

### Post by cong06 on 2010-03-26
I assume you have no idea why it happened, otherwise you would have posted...

Did you try reinstalling update-manager? Maybe also python-2.6?

Though someone else might know more how to respond to that error then me...

---

### Post by darolu on 2010-03-26
nvm cong06 beat me to it

---

### Post by esky64 on 2010-03-26
> **cong06 said:**
> I assume you have no idea why it happened, otherwise you would have posted...

Did you try reinstalling update-manager? Maybe also python-2.6?

Though someone else might know more how to respond to that error then me...

Correct I have no idea why it is not working one day it was the next it was not
My system has been very unstable but today with a new update it looks like it may now be stable again.


chris@chris-desktop:~$ sudo apt-get install  update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jmszr on 2010-03-26
esky64,

Do the Synaptic Package Manager and the Software Center work?

---

### Post by cong06 on 2010-03-26
> **esky64 said:**
> chris@chris-desktop:~$ sudo apt-get install  update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

My bad I meant to run this:
```

sudo apt-get reinstall update-manager python2.6

```

Do you know of any other python programs are screwed up? try something like alacarte...I think alot of "System > Preferences/Adminstration" programs use python.
Maybe go through them and see if any other are broken?

---

### Post by esky64 on 2010-03-26
> **cong06 said:**
> My bad I meant to run this:
```

sudo apt-get reinstall update-manager python2.6

```

Do you know of any other python programs are screwed up? try something like alacarte...I think alot of "System > Preferences/Adminstration" programs use python.
Maybe go through them and see if any other are broken?

chris@chris-desktop:~$ sudo apt-get reinstall update-manager python2.6
[sudo] password for chris: 
E: Invalid operation reinstall

---

### Post by cong06 on 2010-03-26
> **esky64 said:**
> chris@chris-desktop:~$ sudo apt-get reinstall update-manager python2.6
[sudo] password for chris: 
E: Invalid operation reinstall

That'll teach me to actually test commands before I type them.
What I really meant was "aptitude":
```

sudo aptitude reinstall update-manager python2.6

```

I'm surprised apt-get doesn't have a re-install feature...

---

### Post by esky64 on 2010-03-26
> **jmszr said:**
> esky64,

Do the Synaptic Package Manager and the Software Center work?
Synaptic Package Manager works 
still to test Software Center

---

### Post by esky64 on 2010-03-26
thanks cong06
I reinstalled update-manager but still not working

---

### Post by AndyDeGroo on 2010-03-26
> **esky64 said:**
> thanks cong06
I reinstalled update-manager but still not working
You should try reinstalling python2.6 as well.
If you want to get updates without update manager, go into Synaptic then Edit > Mark All Upgrades or Ctrl+G and click apply.

---

### Post by esky64 on 2010-03-26
> **AndyDeGroo said:**
> You should try reinstalling python2.6 as well.
If you want to get updates without update manager, go into Synaptic then Edit > Mark All Upgrades or Ctrl+G and click apply.
Tried that thanks nothing to upgrade
chris@chris-desktop:~$ sudo aptitude reinstall update-manager python2.6
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  python2.6 update-manager 
0 packages upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/3,297kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 173578 files and directories currently installed.)
Preparing to replace python2.6 2.6.4-0ubuntu3 (using .../python2.6_2.6.4-0ubuntu3_amd64.deb) ...
Unpacking replacement python2.6 ...
Preparing to replace update-manager 1:0.126.9 (using .../update-manager_1%3a0.126.9_all.deb) ...
Unpacking replacement update-manager ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up python2.6 (2.6.4-0ubuntu3) ...

Setting up update-manager (1:0.126.9) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

chris@chris-desktop:~$ 
Still update-manager will not open

BTW thanks to everyone that is trying to help

---

### Post by wojox on 2010-03-26
Alt + F2

Type in: **update-manager** 

Anything?

---

### Post by AndyDeGroo on 2010-03-26
I did some googling for last line of backtrace that you provided.
There are few results popping up, but nothing significant related to update-manager.
Error happens in puthon2.6 gettext library.

This should be reported as bug of update-manager package.
to do that run:
```
ubuntu-bug update-manager
```You may have to register on lauchpad if you don't have account there.
I searched on lauchpad but no similar bugs came up so it is safe to assume that this is a bug.

And **remember to add that backtrace** to bug report. That can help a lot.

To me this looks like a bug in pythons gettext.py in some obscure circumstances when/if erroneous string is passed to gettext._parse() function and in this case the sting is program arguments which is empty or could contain whitespace.

And one more thing - **please be more descriptive when you write titles**. Thanks :)

---

### Post by AndyDeGroo on 2010-03-26
Narrowed down to:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/452021](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/452021)

On launchpad that's as close as can get.

IMHO Error is related to faulty locale mo file. I suppose your locale is something like en_AU.
Try to change locale and see if it solves problem.

My locale is en_US.UTF-8 and update-manager works fine.

---

### Post by esky64 on 2010-03-26
> **wojox said:**
> Alt + F2

Type in: **update-manager** 

Anything?

MM Nothing at all

---

