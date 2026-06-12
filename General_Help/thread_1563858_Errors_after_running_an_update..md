---
title: "Errors after running an update."
date: 2010-08-29
forum: General Help
---

### Post by false_chicken on 2010-08-29
I ran an update recently. It was about a 300Mb download and with it was the current kernel and others. I restarted to find an error. Compiz is no longer starting and there is this red minus icon on my bar saying there is a package error. It said to run "sudo dpkg --configure -a" but when I ran that I got: dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory" Any Ideas? Thanks.

Running Lucid i386 Desktop.

---

### Post by dabl on 2010-08-29
Close synaptic, and open a terminal.

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get autoremove
```

now try ```
sudo dpkg --configure -a
```

post back if you have errors.

---

### Post by false_chicken on 2010-08-29
Same error on all but the first command: "dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory" I checked and the file status indeed does not exist.

---

### Post by false_chicken on 2010-08-29
So do I reinstall? Because I would hate to have to do that.

---

### Post by JBAlaska on 2010-08-29
Don't re-install, this can be fixed.

Try:
```
sudo dpkg-reconfigure -phigh apt

```

---

### Post by false_chicken on 2010-08-29
This is what I got: 

"Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 1.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 2.
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 70, <$__ANONIO__> chunk 2.
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt is not installed"

---

### Post by JBAlaska on 2010-08-29
Ok,
1- gunzip **dpkg.status.0.gz** located in **/var/backups** and save it as "**status**" in **/var/lib/dpkg/**

2- you also might need to create the "**available**" file in **/var/lib/dpkg/** this can be done by typing: ```
sudo touch available
```

Then:
```
sudo dpkg --configure -a
```

---

### Post by false_chicken on 2010-08-29
Thanks! that problem is fixed. But now it says I have about 14 broken packages. And I dont know what to do about them. If I choose reinstall it seems to want to pretty much reinstall my whole system.

---

### Post by JBAlaska on 2010-08-29
Open synaptic package manager in **System, Administration**
And click edit, fix broken packages.

---

