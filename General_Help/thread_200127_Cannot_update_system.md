---
title: "Cannot update system"
date: 2006-06-19
forum: General Help
---

### Post by Grog140 on 2006-06-19
I got a message I needed updates but one couldn't be installed. So I went into a terminal and did "sudo apt-get upgrade" and got this:

```
matthew@matthew-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libwnck18
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

I tried doing a sudo apt-get build-dep libqnck18 and got back this:
```
matthew@matthew-laptop:~$ sudo apt-get build-dep libwnck18
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

And I did a sudo apt-get install libqwnck18 and got bacK:

```
matthew@matthew-laptop:~$ sudo apt-get install libwnck18
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libwnck18: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
E: Broken packages

```

Can anyone give me a hand please? I am out of ideas.

---

### Post by joshrobinson on 2006-06-19
looks like the version of libpango yo need isnt available yet in the repo

have you tried
sudo apt-get dist-upgrade

---

### Post by Grog140 on 2006-06-19
Yeah, I got the same message as when I did the apt-get upgrade.

---

### Post by Bubbles on 2006-06-19
I'm experiencing exactly the same problem.

---

### Post by Grog140 on 2006-06-20
With the same package as well?

---

### Post by Bubbles on 2006-06-20
Yes, 'tis the same.

---

### Post by mingster on 2006-06-27
same here... this is really damn annoying :evil:

---

### Post by Ramses de Norre on 2006-06-27
I'd say wait untill all dependencies are in the repos or do a dist-upgrade which will most likely install the package but it could break some things..

---

### Post by Grog140 on 2006-07-05
I got the problem fixed. I installed a package manually. I installed "libfontconfig-dev", after I did that Ubuntu nitified me of an update and I no longer get an error.

If you diddn't fix the problem yet then I beleive this is what worked for me. And the problem lied somewhere in XGL/Compiz I discovered today as well.

---

