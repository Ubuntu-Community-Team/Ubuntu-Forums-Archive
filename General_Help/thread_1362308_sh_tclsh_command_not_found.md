---
title: "sh: tclsh: command not found"
date: 2009-12-23
forum: General Help
---

### Post by shariefbe on 2009-12-23
Hello i am trying to install LTIB for my AMR processor. While i compile the file i am getting the below error.
```

sh: tclsh: command not found

ltib cannot be run because one or more of the host packages needed to run it
are either missing or out of date or not in ltib's standard path.  Please
install/upgrade these packages on your host.  If you have your own utilities
in non-standard paths, please add an entry into the .ltibrc file for example:

%path_std
/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/X11R6/bin:/my/own/exes

```
I dont know what will be the error. Can anyone help how to fix this problem?

---

### Post by Mister.Vash on 2009-12-23
Sounds like you are missing the package tcl
Install it from Synaptic Package Manager or from the command line
sudo apt-get install tcl

---

### Post by shariefbe on 2009-12-23
Yes thank you. Now i fixed that problem. But i am getting the remainig all the rrors which i have posted. ```

ltib cannot be run because one or more of the host packages needed to run it
are either missing or out of date or not in ltib's standard path.  Please
install/upgrade these packages on your host.  If you have your own utilities
in non-standard paths, please add an entry into the .ltibrc file for example:

%path_std
/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/X11R6/bin:/my/own/exes
```
Please help me

---

