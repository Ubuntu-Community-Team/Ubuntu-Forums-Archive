---
title: "Accidentally deleted /usr/share/applications"
date: 2010-01-04
forum: General Help
---

### Post by niekez on 2010-01-04
I stupidly removed my /usr/share/applications using sudo rm -rf. How bad is this an is there a way to quickly fix it? Thanks!

---

### Post by Barriehie on 2010-01-04
> **niekez said:**
> I stupidly removed my /usr/share/applications using sudo rm -rf. How bad is this an is there a way to quickly fix it? Thanks!

Oops...  Have a backup???  :) Try this from the terminal and see if it yields a list of what's supposed to be installed.
```

dpkg --get-selections > *SomeFileName*
```

Edit: Don't feel bad, I one time was testing a script and renamed EVERY file/folder in my home dir with a random 10 character name...

---

### Post by VCoolio on 2010-01-04
Not too bad, there are .desktop files in there for a lot of installed apps, but it may screw up your menus. I've attached the contents of my /usr/share/applications; it has the default karmic ones in there, plus of course a lot of stuff I installed; but you can pick what you need.

---

### Post by Barriehie on 2010-01-04
So the ```
dpkg --get-selections > *SomeFileName*
``` should've, hopefully, returned something like this:
```

...
acl						install
acpi						install
acpi-support					install
acpid						install
acroread					install
adduser						install
alacarte					install
...

```

If it did, and SHOULD, then we can run a command to reinstall those packages.

---

### Post by Seq on 2010-01-04
> **Barriehie said:**
> So the ```
dpkg --get-selections > *SomeFileName*
``` should've, hopefully, returned something like this:
```

...
acl						install
acpi						install
acpi-support					install
acpid						install
acroread					install
adduser						install
alacarte					install
...

```

If it did, and SHOULD, then we can run a command to reinstall those packages.

You don't need to know all installed packages, just packages that installed files to /usr/share/applications.
```
dpkg-query -S /usr/share/applications/
```

---

### Post by Seq on 2010-01-04
> **Seq said:**
> You don't need to know all installed packages, just packages that installed files to /usr/share/applications.
```
dpkg-query -S /usr/share/applications/
```

To be slightly more complete, a some quick and ugly sed use gets us the following command which should reinstall all packages that have files in /usr/share/applications

```
dpkg-query -S /usr/share/applications/ | sed -e "s/:.*$//" -e "s/,//g" | xargs sudo aptitude reinstall
```

---

### Post by niekez on 2010-01-10
Thanks for all the replies.

> **Seq said:**
> To be slightly more complete, a some quick and ugly sed use gets us the following command which should reinstall all packages that have files in /usr/share/applications

```
dpkg-query -S /usr/share/applications/ | sed -e "s/:.*$//" -e "s/,//g" | xargs sudo aptitude reinstall
```


It says only the gimp and epiphany installed files there, weird huh?
And my desktop is corrupted, I get the login screen but after I log in, the only thing I see is my wallpaper.

---

### Post by Seq on 2010-01-10
> **niekez said:**
> Thanks for all the replies.




It says only the gimp and epiphany installed files there, weird huh?
And my desktop is corrupted, I get the login screen but after I log in, the only thing I see is my wallpaper.

Indeed that is weird. I get 167 packages needing re-install. I even get two packages listed on a headless server without X.

Was the two packages from the dpkg-query command itself, or was it an error in the parsing code?

```
dpkg-query -S /usr/share/applications/
```

You should get a fair number of hits here.

---

