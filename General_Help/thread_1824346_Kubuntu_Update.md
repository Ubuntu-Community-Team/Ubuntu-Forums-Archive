---
title: "Kubuntu Update"
date: 2011-08-13
forum: General Help
---

### Post by rf.bennett1 on 2011-08-13
Hi everyone

I'm trying to update Kubuntu 11.04 here is my error:

 p, li { white-space: pre-wrap; }  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



here is what i have tried to fix it:
robert@Kubuntu:~$ sudo dpkg --configure-a
[sudo] password for robert: 
dpkg: error: unknown option --configure-a

Type dpkg --help for help about installing and un-installing packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !


Hey Ideas

Thanx :)

---

### Post by snowpine on 2011-08-13
Instead of this:

```
sudo dpkg --configure-a
```

Try this: 

```
sudo dpkg --configure -a
```

---

### Post by rf.bennett1 on 2011-08-13
Fixed!!!

You are a legend

Respect!!

:)))

---

