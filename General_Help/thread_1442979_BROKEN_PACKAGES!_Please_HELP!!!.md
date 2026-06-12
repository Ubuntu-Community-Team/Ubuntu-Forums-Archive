---
title: "BROKEN PACKAGES! Please HELP!!!"
date: 2010-03-30
forum: General Help
---

### Post by systemOAD on 2010-03-30
hello all, recently i installed pyserial2.4 and after that i cannot install any new packages. my system says there is 15 broken packages and i have tried to fix them in synaptic and ive followed this: [http://ubuntuforums.org/showthread.php?t=252762](http://ubuntuforums.org/showthread.php?t=252762) and i have followed other threads as well. nothing helped. the output of synaptic is the following:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 18893 package 'libcryptui0':
 newline in field name `$.'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18893 package 'libcryptui0':
 newline in field name `$.'

Can someone please help?

---

### Post by plucky on 2010-03-30
> **systemOAD said:**
> hello all, recently i installed pyserial2.4 and after that i cannot install any new packages. my system says there is 15 broken packages and i have tried to fix them in synaptic and ive followed this: [http://ubuntuforums.org/showthread.php?t=252762](http://ubuntuforums.org/showthread.php?t=252762) and i have followed other threads as well. nothing helped. the output of synaptic is the following:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 18893 package 'libcryptui0':
 newline in field name `$.'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18893 package 'libcryptui0':
 newline in field name `$.'

Can someone please help?

Try this from a terminal

```
cd /var/lib/dpkg
sudo cp status status.backup
sudo cp status-old status
sudo apt-get update
```

The first sudo command will ask for your password,which it will not echo,when you type it in.

If you get no errors with the "update" command then you should be good to go and you can ignore the rest of the information.

And if that doesn't work,then restore the **status.backup** back to **status** and then from a terminal ```
gksudo gedit /var/lib/dpkg/status
``` and search for "line 18893" and delete all the information for the package "libcryptui0"


Good Luck

---

### Post by systemOAD on 2010-03-30
That worked! Thanks!!! :d

---

### Post by eotakos on 2010-03-30
remember to use the "thread tools" drop-down menu on the right-hand side of the topic page, to mark your threads as "SOLVED" when you consider them as such. :-)

---

