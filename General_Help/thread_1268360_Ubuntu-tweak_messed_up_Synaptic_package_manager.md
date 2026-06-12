---
title: "Ubuntu-tweak messed up Synaptic package manager"
date: 2009-09-16
forum: General Help
---

### Post by wclathan on 2009-09-16
Whenever I try to run the Synaptic Package manager I get the following error.

E: the package for ubuntu-tweak needs to be reinstalled, but I can't find an archive for it
E: Internal error opening cache (1).  Please report

What have I done wrong?  How do I fix this?

---

### Post by por100pre1 on 2009-09-16
Welcome to the Forums. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak
```

Please post the result.

---

### Post by fanglinyong on 2009-09-16
can you run ubuntu-tweak software?

---

### Post by wclathan on 2009-09-17
> **por100pre1 said:**
> Welcome to the Forums. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak
```Please post the result.

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 133320 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak

---

### Post by wclathan on 2009-09-17
> **fanglinyong said:**
> can you run ubuntu-tweak software?
kind of.  Ubuntu tweak runs, but most of the options I choose aren't executed

---

### Post by tsikpemoise on 2009-09-17
I have the same problem. In fact, i installed a wrong version of ubuntu-tweak : ubuntu-tweak_0.4.9-1~karmic1_i386.

Any idea of how to remove this ?
Thanks

---

### Post by por100pre1 on 2009-09-17
Where did you get that version of Ubuntu Tweak?

Maybe adding the Ubuntu Tweak repository can help you to reinstall:

[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by wclathan on 2009-09-17
> **por100pre1 said:**
> Where did you get that version of Ubuntu Tweak?

Maybe adding the Ubuntu Tweak repository can help you to reinstall:

[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)
tried it.  No change.  Even with the repositories added in, it won't let me reinstall the package

---

### Post by wilee-nilee on 2009-09-17
Try sudo aptitude purge ubuntu-tweak, then restart the computer to clear any cache and try the install again.
 
I'm sure there is a command line to clear the cache of downloads I just don't know what it is.

---

### Post by wclathan on 2009-09-18
> **wilee-nilee said:**
> Try sudo aptitude purge ubuntu-tweak, then restart the computer to clear any cache and try the install again.
 
I'm sure there is a command line to clear the cache of downloads I just don't know what it is.
That's not really the problem I'm having,  My problem is that ubuntu-tweak is causing the Synaptic Package manager to not start.

---

### Post by pyroclastic on 2009-09-18
> **wclathan said:**
> Whenever I try to run the Synaptic Package manager I get the following error.

E: the package for ubuntu-tweak needs to be reinstalled, but I can't find an archive for it
E: Internal error opening cache (1).  Please report

What have I done wrong?  How do I fix this?


Hi, i had the same problem, i just reinstalled the karmic vers. and SPM was back to normal, and i could open it. u can fine the karmic vers [URL="http://ubuntuforums.org/newreply.php?do=newreply&p=7961493"]here :lolflag:
[/URL]

---

### Post by cmcanulty on 2009-09-18
I can't remove or add anything in synaptic as I just get the above error message even after all the above commands being done everything in synaptic except the error message is greyed out.. What a mess! I mistakenly downloaded the 9.10 version of tweak. If system breaks this easily it isn't worth the trouble.Here is what I get with the forced removal, I also deleted the file in tmp. Synaptic still won't run
cmcanulty@Gateway:~$ sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 131244 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
cmcanulty@Gateway:~$

---

### Post by fcuk112 on 2009-09-18
have you tried removing the /usr/share/python-support/ubuntu-tweak.private file and then do sudo apt-get remove ubuntu-tweak?  i think that's what worked for me.

---

### Post by wclathan on 2009-09-19
> **fcuk112 said:**
> have you tried removing the /usr/share/python-support/ubuntu-tweak.private file and then do sudo apt-get remove ubuntu-tweak?  i think that's what worked for me.

That worked! (after a little bit of fussing)  What I had to do was make Ubuntu check for upgrades, agree to a partial upgrade and then tell it to remove the flawed version of Ubuntu-tweak.  Thanks to all!  I appreciate all the input you've given me over this!

---

### Post by cmcanulty on 2009-09-19
I also tried it no change but I get this from terminal.unfortunately with being unable to open synaptic I am stuck
cmcanulty@Gateway:~$ sudo apt-get remove ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.

---

### Post by cmcanulty on 2009-09-19
After restart system OK not sure what fixed it but maybe last above, thanks to all!

---

