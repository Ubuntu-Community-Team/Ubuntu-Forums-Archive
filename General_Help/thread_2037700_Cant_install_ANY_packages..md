---
title: "Cant install ANY packages."
date: 2012-08-05
forum: General Help
---

### Post by Dawnbandit on 2012-08-05
Recently when trying install dependencies (that mysteriously disappeared) it wont work and I this error ```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 54812 package 'libmjpegtools-1.9':
 EOF during value of field `Description' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)

```I've tried sudo apt-ge update but it still doesn't work. 
I've even tried what [this]("http://ubuntuforums.org/showthread.php?t=1635518") thread told me but then I get this error.
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
cp: reading `/var/lib/dpkg/status-old': Input/output error

```](*,)
And also I've had a lot of system problem messages, so I want to upgrade from 12.04 to 12.10 to maybe stop those, but being unable to install packages I can't... 
Any help will be appreciated.

---

### Post by raja.genupula on 2012-08-05
[http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)

---

### Post by Dawnbandit on 2012-08-05
> **raja.genupula said:**
> [http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)
I tried doing those instructions but they didnt work. :(
Now I get this error```
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.

```

---

### Post by raja.genupula on 2012-08-07
do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```
Then try again .

---

