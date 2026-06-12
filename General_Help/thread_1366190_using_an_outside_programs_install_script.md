---
title: "using an outside programs install script"
date: 2009-12-28
forum: General Help
---

### Post by rstrothe on 2009-12-28
I am trying to load a perl based program (PerlSpeaksNonmem).  Developers include an install script install.pl.  when I try to run this script, I have to run it as sudo (i.e. sudo perl install.pl), it gets to a point where it asks to create a directory. but it cannot do so (I think because the sudo has timed out).  What is the best way to do this?

---

### Post by mgol on 2009-12-28
Try su instead:
```

sudo su
perl install.pl
exit

```
Don't forget to exit so that You don't work as root.

---

### Post by audiomick on 2009-12-28
I believe you can get to "su" by using
```
sudo su
```
without creating a root password.

Try that and then your "perl install" command.

I don't think sudo "times out" whilst it is executing something.

---

### Post by mgol on 2009-12-28
Right, I have forgotten about that. :)

---

### Post by 3rdalbum on 2009-12-28
> **rstrothe said:**
> I am trying to load a perl based program (PerlSpeaksNonmem).  Developers include an install script install.pl.  when I try to run this script, I have to run it as sudo (i.e. sudo perl install.pl), it gets to a point where it asks to create a directory. but it cannot do so (I think because the sudo has timed out).  What is the best way to do this?

If you run the script with 'sudo', then it retains root privileges, and all programs it runs will also run with root privileges.

So, this is not the reason why the directory isn't being created.

---

### Post by rstrothe on 2009-12-29
last person was correct -it wasn't a sudo problem - the installer defaulted to a directory to look for perl, but mine is in a different place - sorted now

---

