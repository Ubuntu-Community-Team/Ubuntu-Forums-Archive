---
title: "dpkg broken"
date: 2009-08-05
forum: General Help
---

### Post by sn4re on 2009-08-05
Hi,

sorry for the extremely non-descript thread title, but i can't think of any other way to say it.

Basically dpkg is broken and it is effecting(sp?) every package management system I have (apt-get, add/remove, synaptic), which all used to work just fine. I admit that this problem did surface after my computer froze up and I had to do a not-so-clean reboot, but that has happened many times, and no such problems yet.

When I try to install/remove anything at all, it gives me the following error:
```
(Reading database ... 
dpkg: serious warning: files list file for package `pxljr' missing, assuming package has no files currently installed.
dpkg: unrecoverable fatal error, aborting:
 files list file for package `iproute' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```It used to say something about a stale NFS fine handle about the "pxljr" package, but a fsck cleared that up, yet now I have this new problem.

I myself thought about just reinstalling dpkg somehow, because to me it seems the whole /var/lib/dpkg/info dir is messed up - but I don't know how to do that, quite new to Linux. If there's a less drastic way, I'd love to try it out.

Thanks for any help - getting desperate here (don't want to reinstall again).

Using Ubuntu 9.04 AMD64.

EDIT: see post #3 for solution

---

### Post by soapBAR2 on 2009-08-05
Hi,

This thread may be useful to you.

[HTML]http://ubuntuforums.org/showthread.php?t=679113[/HTML]

(Summarised) - you may be able to recover your dpkg from an old copy using

```
ls -la /var/lib/dpkg
```

or you could nick a copy off a LiveCD. 

PS. To search for files from a ubuntu shell, use "locate yourqueryhere". Use "updatedb" if the results are stale.

---

### Post by sn4re on 2009-08-05
Thanks for the link - it proved very useful. (Can't believe I didn't find it myself :P).

For anybody else having this kind of problem, here's my solution:

Since iproute was giving my this trouble I just "mkdir /home/<name>/backup ; sudo mv /var/lib/dpkg/info/iproute.* /home/<name>/backup/"

After I that it gave me the same error with python-debian - did the same with python-debian.*

That got rid of the errors, so I could use dpkg again. (Mind you, it was still giving me serious warnings about "pxljr", "iproute" and "python-debian").

After that I reinstalled dpkg from the Live CD (just for good measure) and did "sudo apt-get install --reinstall <pkg>" on the 3 broken packages (You can probably use it to reinstall dpkg too, if you don't have a Live CD on hand). If all works well you can "rm -r /home/<name>/backup"

Thanks again, for directing me to that link!

---

