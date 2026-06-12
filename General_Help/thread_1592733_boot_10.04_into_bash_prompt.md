---
title: "boot 10.04 into bash prompt"
date: 2010-10-10
forum: General Help
---

### Post by oospill on 2010-10-10
hi, I was wondering what it would take to have my ubuntu desktop 10.04 boot to the bash prompt instead of loading X.  it would be nice if it would load all the networking stuff, too, hopefully everytrhing but X.

thanks!!

---

### Post by garvinrick4 on 2010-10-10
> **oospill said:**
> hi, I was wondering what it would take to have my ubuntu desktop 10.04 boot to the bash prompt instead of loading X.  it would be nice if it would load all the networking stuff, too, hopefully everytrhing but X.

thanks!! I do believe you choose alternative installation disk.

[Complete Download Options List | Ubuntu]("http://www.ubuntu.com/getubuntu/downloadmirrors#wubi")

---

### Post by gmargo on 2010-10-11
There are at least two simple ways to prevent X from starting at boot time.

1. Remove the contents of the **/etc/X11/default-display-manager** file:
```

$ sudo mv /etc/X11/default-display-manager /etc/X11/default-display-manager.orig
$ sudo touch /etc/X11/default-display-manager

```After you reboot you may have to switch to the text console with ALT-F1 to the get the login prompt.

2. Alternatively, you could remove the **gdm** (or **kdm**) package.

In either case, after you log in, from the command line you can run the **startx** command to start an X11 session.

---

