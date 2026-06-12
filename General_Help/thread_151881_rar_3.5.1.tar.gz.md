---
title: "rar 3.5.1.tar.gz"
date: 2006-03-28
forum: General Help
---

### Post by DemonOfElru on 2006-03-28
well, i am trying to install RAR so i can extract an iso i downloaded. ](*,) but i cant figure out in sudo or not how to do it, i am still a little newbish at linux,

HELP!!

---

### Post by taurus on 2006-03-28
If you want to extract an iso file, why not mount it as
```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop filename.iso /mnt/iso
cd /mnt/iso
ls -la

```
Otherwise, if you want to build or extract rar, do
```

tar xvzf rar_3.5.1.tar.gz
cd rar_3.5.1

```
Then, read either README or INSTALL in there on how to install it...

---

### Post by DemonOfElru on 2006-03-28
well the iso is an operationg system i needto extract and burn to cd so i can boot from it and install it. any suggestion because the readme file is no help.

any sugestions, cause the iso is contained in a multi-part rar file.

---

### Post by cjazz on 2006-03-28
If all you want to do is extract a .rar file, I would install the program unrar, using Snyaptic. That would be unrar-free if for files compressed using rar version below 3.0 or unrar-nonfree for all files. Unrar-nonfree is probably safest. You need to enable multiverse in order to find it.

There's a nice How-To on enabling extra repositories here:
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by DemonOfElru on 2006-03-28
how do i install unrar?
and i have enabled/updated the extra repositories

---

### Post by Sutekh on 2006-03-29
[QUOTE=DemonOfElru]how do i install unrar?
and i have enabled/updated the extra repositories[/QUOTE]
If you have the universe and multiverse repositories enabled then use
```
sudo apt-get install rar unrar-free unrar-nonfree
```
 - You don't have to install all those packages, just remove the name of any you don't wish to install.

---

### Post by artifex on 2006-03-29
[QUOTE=Sutekh]If you have the universe and multiverse repositories enabled then use
```
sudo apt-get install rar unrar-free unrar-nonfree
```
 - You don't have to install all those packages, just remove the name of any you don't wish to install.[/QUOTE]

I think universe and multiverse are enabled. I did 'apt-get clean' 'apt-get autoclean' 'apt-get update'.

```
egrep -v '^#' sources.list

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

```
apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
```

Any idea? BTW, I am able to install unrar-free but that isn't enough for me. Thanks!

---

### Post by DemonOfElru on 2006-03-29
[QUOTE=Sutekh]If you have the universe and multiverse repositories enabled then use
```
sudo apt-get install rar unrar-free unrar-nonfree
```
 - You don't have to install all those packages, just remove the name of any you don't wish to install.[/QUOTE]

OMG thank you soooo much!=D> now i can get that other os installed and load up my games i been missing!\\:D/

---

### Post by Sutekh on 2006-03-29
[QUOTE=artifex]
```

deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

...

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```
[/QUOTE]
You need to add **multiverse** to these lines.  

The other lines with multiverse were the breezy-backports, not the normal breezy repository

---

