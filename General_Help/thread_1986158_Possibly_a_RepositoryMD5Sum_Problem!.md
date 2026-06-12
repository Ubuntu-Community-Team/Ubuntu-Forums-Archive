---
title: "Possibly a Repository/MD5Sum Problem!"
date: 2012-05-24
forum: General Help
---

### Post by thazsar on 2012-05-24
Hey everyone,
I'm still semi-new to Ubuntu and cannot find the answer to my problem so I'm gonna try here!
 
I have a public Repository that I originally created on my 'home' computer using the latest version of Ubuntu . The repository is web-based and hosts Debian Packages. 
The repo contains: 
[LIST]
[*]deb_files folder (which holds all .deb files)
[/LIST]
[LIST]
[*]en_US.bz2 file
[/LIST]
[LIST]
[*]Packages file
[/LIST]
[LIST]
[*]Packages.bz2 file
[/LIST]
[LIST]
[*]Release file
[/LIST]
[LIST]
[*]Release.gpg file
[/LIST]I used MD5Sum checking for authenticating.
 
**THE PROBLEM:** I can only use the 'home' computer to create my 'Packages' file or else it throws a 'Size Mismatch' error. Each computer I use generates a MD5Sum tag that is different from the other computers so I can't upload/install .deb packages from any other computer but my 'home' computer?!?!?
 
*I'm trying to find out if I can either:*
1. Completely remove MD5Sum checking from Ubuntu on my 'home' computer
 
OR
 
2. Allow multiple MD5Sum tags to be accepted during the 'Packages' creation.
 
I use this to create my 'Packages' file:
 
```
 
cd /home/MYCOMPUTER/MyRepo
dpkg-scanpackages . /dev/null -->Packages

``` 
Thanx in advance for any help!!!

---

