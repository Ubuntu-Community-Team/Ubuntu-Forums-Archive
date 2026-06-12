---
title: "How do you fix the error “E: Unmet dependencies.”?"
date: 2011-01-03
forum: General Help
---

### Post by 666f6f on 2011-01-03
Hi all,

When I try to install a software package I get the error E: Unmet dependencies. Try 'apt-get -f install' with no packages. I did try apt-get -f install but that didn't work.

The problem appeared after installing a modified version of [libapache2-mod-wsgi]("http://packages.ubuntu.com/maverick/libapache2-mod-wsgi"). 

I modified the package dependencies because, as you can see from the package details link, it depends on python 3. A version of python is required but not version 3 necessarily and I didn't want to install version 3. There's [bug #672901]("https://bugs.launchpad.net/ubuntu/+source/mod-wsgi/+bug/672901") that describes the problem.

So, modifying the package dependencies allowed me to install libapache2-mod-wsgi without installing python 3 but now I can't install anything else.. How can I fix that?

Thank you.

---

### Post by Rubi1200 on 2011-01-04
Try this and post the output if there are errors:

```
sudo dpkg --configure -a
```

Thanks.

---

### Post by 666f6f on 2011-01-04
> **Rubi1200 said:**
> Try this and post the output if there are errors:

```
sudo dpkg --configure -a
```

Thanks.

Hello Rubi1200,

Here's the output:

```

dpkg: dependency problems prevent configuration of libapache2-mod-wsgi:
 libapache2-mod-wsgi depends on libpython3.1 (>= 3.1); however:
  Package libpython3.1 is not installed.
dpkg: error processing libapache2-mod-wsgi (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache2-mod-wsgi

```

I assume dpkg keeps a list/registry of packages/dependencies and it queries it before each significant package operation in order to verify the consistency of the system.

Can anybody verify this? If this is correct, where is this registry found?

Thank you.

---

### Post by 666f6f on 2011-01-04
Anyone please?

---

### Post by psusi on 2011-01-04
If it requires python 3, then it requires python 3.

sudo apt-get install libpython3.1

---

### Post by mc4man on 2011-01-04
Open your modified .deb w/ archive manager, copy and  post the control file (/DEBIAN/control

Edit (you didn't inadvertently update (or attempt to), back to the repo version?

---

### Post by 666f6f on 2011-01-04
> **psusi said:**
> If it requires python 3, then it requires python 3.

sudo apt-get install libpython3.1

psusi, thank you for you response but that doesn't help me in any way.

---

### Post by psusi on 2011-01-04
> **666f6f said:**
> psusi, thank you for you response but that doesn't help me in any way.

Why not?  Did you try it?

---

### Post by 666f6f on 2011-01-04
> **psusi said:**
> Why not?  Did you try it?

Because the package shouldn't require python3, it is a bug that it is a dependency, and I don't want to install python3.

---

### Post by psusi on 2011-01-04
> **666f6f said:**
> Because the package shouldn't require python3, it is a bug that it is a dependency, and I don't want to install python3.

Why do you say that?  It wasn't packaged to depend on python 3 just for grins, it was packaged to depend on python 3 because it doesn't work without it.  Python 3.x and 2.x are not compatible.

---

### Post by 666f6f on 2011-01-04
> **psusi said:**
> Why do you say that?  It wasn't packaged to depend on python 3 just for grins, it was packaged to depend on python 3 because it doesn't work without it.  Python 3.x and 2.x are not compatible.

I tried to write a complete first post, please have a look at it. If you think I've missed something, then you can yell at me :)

---

### Post by 666f6f on 2011-01-04
> **mc4man said:**
> Open your modified .deb w/ archive manager, copy and  post the control file (/DEBIAN/control

I deleted the file after installation.

> **mc4man said:**
> Edit (you didn't inadvertently update (or attempt to), back to the repo version?

/var/lib/dpkg/status and /var/lib/dpkg/available is the dpkg cache/library I was searching for and they report the *unmodified* dependencies.

I haven't updated the system, at least not deliberately, but I did do apt-get update. Maybe that action caused an update of the status and available files.

I guess that if I modify those those, I'll fix my system for a while, until I run apt-get update again..

---

### Post by mc4man on 2011-01-04
> but I did do apt-get update.
A 'modified' .deb (editing the control file), will be seen as the same version when installing.
However AFTER installing the repo version will be seen as an update to the modded one.

See screen where I modded your package, now seen as upgradeable (and I have no issues with dpkg, apt or synaptic

The control as i edited it
> Installed-Size: 392
Depends: apache2, apache2.2-common, libc6 (>= 2.4), libpython2.6 (>= 2.6), python (>= 2.6)
Suggests: apache2-mpm-worker | apache2-mpm-event


---

### Post by 666f6f on 2011-01-04
Hi mc4man,

thank you for helping me out!

> **mc4man said:**
> A 'modified' .deb (editing the control file), will be seen as the same version when installing.
However AFTER installing the repo version will be seen as an update to the modded one.

How did you verify/check that the repo version is seen as an update to the modded one? It seems that mine is not marked as upgradeable.

```

gp@chronos:~$ dpkg -s libapache2-mod-wsgi|grep Status
Status: install ok unpacked

```


> **mc4man said:**
> See screen where I modded your package, now seen as upgradeable (and I have no issues with dpkg, apt or synaptic


Here's my /var/log/dpkg.log.1 output

```

gp@chronos:~$ grep libapache2-mod-wsgi /var/log/dpkg.log.1
2010-12-31 18:54:57 install libapache2-mod-wsgi <none> 3.2-2
2010-12-31 18:54:57 status half-installed libapache2-mod-wsgi 3.2-2
2010-12-31 18:54:58 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:54:58 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:54:58 configure libapache2-mod-wsgi 3.2-2 3.2-2
2010-12-31 18:54:58 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:54:58 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:54:58 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:54:58 status half-configured libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:02 status installed libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:18 upgrade libapache2-mod-wsgi 3.2-2 3.2-2
2010-12-31 18:55:18 status half-configured libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:18 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:18 status half-installed libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:18 status half-installed libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:19 status unpacked libapache2-mod-wsgi 3.2-2
2010-12-31 18:55:19 status unpacked libapache2-mod-wsgi 3.2-2

```

There's un upgrade step write after installation, I wonder if this is normal or not..

---

### Post by mc4man on 2011-01-04
Taking a look on the install where i installed the modified package I can't see where anything concerning an update would cause an issue.

so probably the issue is with the .deb you did install. (was assuming from your launchpad post that all went well

Maybe try searching it in synaptic - if it shows as installed then remove, if not installed then try installing, if synaptic shows any broken packages then let it fix them.

If you can't use synaptic then post back.
(in the long run modifying an already built package is not as good as building to suit

---

### Post by 666f6f on 2011-01-05
> **mc4man said:**
> Taking a look on the install where i installed the modified package I can't see where anything concerning an update would cause an issue.

so probably the issue is with the .deb you did install. (was assuming from your launchpad post that all went well

Maybe try searching it in synaptic - if it shows as installed then remove, if not installed then try installing, if synaptic shows any broken packages then let it fix them.

If you can't use synaptic then post back.
(in the long run modifying an already built package is not as good as building to suit

Thanks mc4man, I'll try your suggestions :)

---

