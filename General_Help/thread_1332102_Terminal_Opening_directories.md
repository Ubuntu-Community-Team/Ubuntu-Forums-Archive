---
title: "Terminal: Opening directories"
date: 2009-11-20
forum: General Help
---

### Post by Stephenbme on 2009-11-20
Hi

I am using a clean install of 9.10 Karmic. I am unable to open directories in the terminal:

stephen@INEXS-desktop:~$ ls
Desktop    examples.desktop      Movie ISO's  Public     zero.trf
Documents  GoogleEarthLinux.bin  Music        Templates
Downloads  Incoming              Pictures     Videos
stephen@INEXS-desktop:~$ cd /Documents
bash: cd: /Documents: No such file or directory
stephen@INEXS-desktop:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
stephen@INEXS-desktop:~$ cd /Incoming
bash: cd: /Incoming: No such file or directory

As a total nube, I would like to figure this out. Any help will be great.

Stephen ](*,)

---

### Post by lisati on 2009-11-20
> **Stephenbme said:**
> Hi

I am using a clean install of 9.10 Karmic. I am unable to open directories in the terminal:

stephen@INEXS-desktop:~$ ls
Desktop    examples.desktop      Movie ISO's  Public     zero.trf
Documents  GoogleEarthLinux.bin  Music        Templates
Downloads  Incoming              Pictures     Videos
stephen@INEXS-desktop:~$ cd /Documents
bash: cd: /Documents: No such file or directory
stephen@INEXS-desktop:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
stephen@INEXS-desktop:~$ cd /Incoming
bash: cd: /Incoming: No such file or directory

As a total nube, I would like to figure this out. Any help will be great.

Stephen ](*,)

Try leaving off the initial "/", you don't need it when moving to a directory/folder contained in the folder you're currently browsing. e.g. ```
cd Documents
```

---

### Post by undecim on 2009-11-20
lisati is correct. Using the / at the beginning of a folder indicates that you want a file/folder at the root of the drive. That is, /Documents/ as opposed to /home/stephan/Documents/

Omitting the / or using ./ indicates that you want a directory inside the directory you are already in. By default, you will be in /home/stephan/, so "Documents" refers to /home/stephan/Documents

You can also use ~/Documents. The ~ expands to your home directory path, and hence ~/Documents becomes /home/stephan/Documents. The great part about that is that it works no matter what directory you are in.

---

### Post by Stephenbme on 2009-11-26
Many thanks :)

---

