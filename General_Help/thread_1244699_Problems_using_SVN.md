---
title: "Problems using SVN"
date: 2009-08-19
forum: General Help
---

### Post by Brian031168 on 2009-08-19
Hi

I have been trying to install enlightenment from svn, all seemed to be going well until the process was interupted (for some reason my comp logged out).
When I tried to restart the process it started ok but then gave me this message:

Checking MISC source ... svn: Working copy 'MISC' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)

and when I try to run svn cleanup I get this:

svn: '.' is not a working copy directory

Any ideas how to fix this problem, whatever it is?

TIA

---

### Post by brij on 2009-08-19
have you tried running svn status? The file which is locked should have L in front of it. Also the error indicates that you are not in the directory Make sure you  have the right path as your svn target when you run svn cleanup

---

### Post by Brian031168 on 2009-08-19
Sorry to be stupid, but how do I know what is the right directory?

---

### Post by andrew.46 on 2009-08-19
Hi Brian,

> **Brian031168 said:**
> Sorry to be stupid, but how do I know what is the right directory?

You are after the directory that holds all the downloaded svn material. I believe the initial download syntax would be:

```
$ svn co http://svn.enlightenment.org/svn/e/trunk/e ***[COLOR="Red"]<name of directory>[/COLOR]***
```

and whatever you have used at that time for *<name of directory>* is the place you should be running the *svn cleanup* command.

Andrew

---

### Post by konqueror7 on 2009-08-19
you can try searching the directory you used by using
```
history | less
```

or just start from scratch again, checkout the repo again to a new directory, instead of having this problem. if its too large, then just continue the cleanup and continue again...

---

