---
title: "Can't Install Packages!"
date: 2006-03-19
forum: General Help
---

### Post by GTar on 2006-03-19
Hey,

I tried to install a package though Synaptic PM The other day and it wouldn't work. It would download the package, attempt to install for a couple of seconds then just exit without any error messages back to the package browser.

Trying to install using apt-get gave this error:
```

Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I need desperatly to install some libraries at the moment, help would be greatly appreciated.

---

### Post by Ramses de Norre on 2006-03-19
Do you have that file?
Does sudo apt-get update work?
Otherwise try this: ```
sudo mv /etc/apt/sources.list ~/sources.list
sudo gedit /etc/apt/sources.list
save this file without typing anything
sudo apt-get update
sudo mv sources.list /etc/apt/sources.list
sudo apt-get update
```

---

### Post by xenmax on 2006-03-19
I am quite new to all this myself, but i read this somewhere which might help:
 Run dselect in interactive mode( type dselect in cmd-line and hit enter)  - this gives a menu of options - select Update option and hit enter - this should create the /var/lib/dpkg/available file

---

### Post by Ramses de Norre on 2006-03-19
Try that first, looks like an easier solution ;)

---

### Post by GTar on 2006-03-19
[QUOTE=xenmax]I am quite new to all this myself, but i read this somewhere which might help:
 Run dselect in interactive mode( type dselect in cmd-line and hit enter)  - this gives a menu of options - select Update option and hit enter - this should create the /var/lib/dpkg/available file[/QUOTE]

Cheers, this worked perfectly. Thanks.

---

