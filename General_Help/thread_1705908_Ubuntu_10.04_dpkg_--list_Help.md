---
title: "Ubuntu 10.04: dpkg --list Help"
date: 2011-03-13
forum: General Help
---

### Post by SexySara on 2011-03-13
How do I slow down the output from the command...
```
dpkg --list
```

... or can I go up the page and back down? AND... can I copy all of this to a text file?

---

### Post by zvacet on 2011-03-13
```
dpkg --list | less
```

and to get file

```
dpkg --list > file.txt
```

If you want to get list of installed packages you can use 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

---

### Post by cipherboy_loc on 2011-03-13
Also, if you are searching for something in particular (say gedit), you can also run:

```

dpkg --list | grep -i 'gedit'

```



Cipherboy

---

### Post by oldfred on 2011-03-13
I use dpkg to list my installed apps, so I can back up the list and use it to reinstall all my apps when I do a clean reinstall. But this is just the package names without the additional info of what it is.

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

But I can run this which give more info.

List with explanations of programs, not it is for reinstall
dpkg -l > ~/installed_programs.txt

And if you have aptitude:
A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

### Post by zvacet on 2011-03-13
Another way to reinstall installed packages is 

```
 aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

Save this file ( send it to yourself by e-mail or some other way) and afte4r installing Ubuntu put that file in your home directory and

```
 sudo xargs aptitude --schedule-only install < my-packages
 sudo aptitude install
```

---

