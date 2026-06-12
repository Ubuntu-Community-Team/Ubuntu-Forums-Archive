---
title: "Updating Filezilla"
date: 2010-09-25
forum: General Help
---

### Post by rmcellig on 2010-09-25
From a newbie:

I have version 3.3.1installedin Ubuntu 10.04. I understand that there is a newer version. What is the easiest way for me to update to the newer version.

---

### Post by Irony on 2010-09-25
Type filezilla in google;

[https://launchpad.net/~yofel/+archive/ppa](https://launchpad.net/~yofel/+archive/ppa)

Or you could just unzip filezilla from here;

[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php)

Extract it and run it directly.

---

### Post by jcolyn on 2010-09-25
The safest way is to enable getdeb.

Google getdeb to find the website.

---

### Post by rmcellig on 2010-09-25
I am  taken to thispage:

[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)

I am not sure where to go from here once I download this file. 

FileZilla_3.3.4.1_i586-linux-gnu.tar.bz2

---

### Post by luigi_mb on 2010-09-25
First move the archive to your home folder. Then unpack it:

```

$ tar xvf FileZilla_3.3.4.1_i586-linux-gnu.tar.bz2

```

Then simply run the executable:

```

$ cd FileZilla3
$ bin/filezilla

```

/luigi

---

### Post by rmcellig on 2010-09-25
Thanks. I will try that. I never installed anything in Ubuntu this way before.

---

### Post by Irony on 2010-09-26
Installing a program is basically a process of unpacking files and placing them in the appropriate place and doing the same with any dependencies.

This usually occurs automatically via synaptic.

Here your installation of filezilla is a simple manual process of unpacking (right click on the zip file and click extract here) then moving the extracted folder to where ever you want it.

You can add a menu entry to link to the executable file. However starting it in terminal is a good first start because it will lead to any clues as to why it doesn't start if it doesn't start.

The same happens in windows, for example keepassx you simply extract and move to program files and then put a shortcut to the executable.

---

