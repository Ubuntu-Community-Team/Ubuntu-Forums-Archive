---
title: "Broken Packages play on linux"
date: 2011-02-22
forum: General Help
---

### Post by EliteLamer on 2011-02-22
How do I fix this? I ran one of the lines for install twice..

> W: Duplicate sources.list entry [http://deb.playonlinux.com/](http://deb.playonlinux.com/) maverick/main amd64 Packages (/var/lib/apt/lists/deb.playonlinux.com_dists_maverick_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
tiako@tiako-EP45-UD3P:~$ apt-get update


I ran apt-get update..

> The following packages have unmet dependencies:
 playonlinux : Depends: python-wxgtk2.8 but it is not installable
E: Broken packages


---

### Post by plucky on 2011-02-22
> W: Duplicate sources.list entry [http://deb.playonlinux.com/](http://deb.playonlinux.com/) maverick/main amd64 Packages 

That means you have the same repository specified twice in either your sources.list or in sources,list.d directory.
Please post output from a terminal for ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

Or open **Software Sources** through Synaptic Package Manager or Software Centre and un-tick one of the playonlinux sources.


Good Luck

---

### Post by EliteLamer on 2011-02-22
> **plucky said:**
> That means you have the same repository specified twice in either your sources.list or in sources,list.d directory.
Please post output from a terminal for ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

Or open **Software Sources** through Synaptic Package Manager or Software Centre and un-tick one of the playonlinux sources.


Good Luck

> total 16
-rw-r--r-- 1 root root 126 2011-02-21 21:16 bisigi-ppa-maverick.list
-rw-r--r-- 1 root root 126 2011-02-21 21:16 bisigi-ppa-maverick.list.save
-rw-r--r-- 1 root root 134 2011-02-21 21:16 docky-core-ppa-maverick.list
-rw-r--r-- 1 root root  46 2011-02-20 02:56 playonlinux.list


Thanks :)

---

### Post by EliteLamer on 2011-02-22
I used Software Sources to uncheck one of the sources as there were two of the same for playonlinux; however, this did not seem to fix the problem as I still receive the same error.

---

### Post by plucky on 2011-02-22
> **EliteLamer said:**
> I used Software Sources to uncheck one of the sources as there were two of the same for playonlinux; however, this did not seem to fix the problem as I still receive the same error.

Which error?

Do you still get the Duplicate sources warning?


If not then for

> The following packages have unmet dependencies:
playonlinux : Depends: python-wxgtk2.8 but it is not installable
E: Broken packages 

Try ```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by EliteLamer on 2011-02-22
> **plucky said:**
> Which error?

Do you still get the Duplicate sources warning?


If not then for



Try ```
sudo apt-get update
sudo apt-get install -f
```


> tiako@tiako-EP45-UD3P:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Dunno..Yeah I still get the same error when trying to 

sudo apt-get install playonlinux

---

### Post by ~LoKe on 2011-02-22
Try
```
sudo apt-get -f install python-wxgtk2.8
```

---

### Post by EliteLamer on 2011-02-22
> **~LoKe said:**
> Try
```
sudo apt-get -f install python-wxgtk2.8
```

Results in..

> Package python-wxgtk2.8 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-wxgtk2.8' has no installation candidate
tiako@tiako-EP45-UD3P:~$ 


---

### Post by plucky on 2011-02-23
Do you have the **universe** repository enabled?

Post output of ```
cat /etc/apt/sources.list
``` 


Or in Software Sources,you could try the Main server if you have the Universe repository enabled.

---

### Post by EliteLamer on 2011-02-23
Thanks everyone for whatever reason "sudo apt-get install playonlinux" worked today. I have no idea why.

---

