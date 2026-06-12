---
title: "Cannot see folder contents"
date: 2011-03-24
forum: General Help
---

### Post by nikhilneela on 2011-03-24
Hi all, I have two operating systems(Ubuntu and Windows). Recently i accessed my ubuntu desktop from windows using ext2explore and from then onwards i am unable to see contents of ubuntu desktop and i am unable to save files on to the desktop. What could be the reason and how do i solve this? Thanks in advance

---

### Post by PCNetSpec on 2011-03-24
Try forcing ubuntu to run fsck at next boot, then reboot:

```
sudo touch /forcefsck
sudo shutdown -r now
```

and see if that fixes it.

---

### Post by nikhilneela on 2011-03-24
hi thanks for the quick reply but the commands didnot work.

---

### Post by PCNetSpec on 2011-03-24
When you say it didn't work, do you mean it didn't run a file system check as it booted, or that the file system check didn't fix the issue?

Can you open a terminal and enter:

```
cd ~
ls -l
```

and post the output.

also enter:

```
gedit ~/.config/user-dirs.dirs
```

and check it contains this line:

> **XDG_DESKTOP_DIR="$HOME/Desktop"**

---

### Post by nikhilneela on 2011-03-25
Here is the output of the commands that u asked

```

nikhil@nikhilneela:~$ cd ~
nikhil@nikhilneela:~$ ls -l
total 8220
-rw-r--r--  1 root   root      1159 2011-03-21 20:03 192.168.10.201
drwxrwxrwx  4 root   root      4096 2011-03-24 07:42 Assignment
-rw-r--r--  1 nikhil nikhil   35950 2011-03-25 00:36 DatabaseMapping.owl
d-wxrwx-wx 20 nikhil nikhil    4096 2011-03-25 00:24 Desktop
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 01:07 Documents
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-24 08:57 Downloads
-rw-r--r--  1 nikhil nikhil     179 2011-03-07 01:02 examples.desktop
-rwxr-xr-x  1 nikhil nikhil    7386 2011-03-07 01:52 gnome-shell-build-setup.sh
-rw-r--r--  1 nikhil nikhil   10030 2011-03-07 02:25 index.html
-rw-r--r--  1 nikhil nikhil   10826 2011-03-07 02:25 index.html.1
drwxr-xr-x  4 nikhil nikhil    4096 2011-03-24 01:11 MT2010056
-rw-r--r--  1 nikhil nikhil   65251 2011-03-24 06:07 MT2010056.tar.bz2
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 01:07 Music
-rwxr-xr-x  1 root   root       106 2011-03-21 20:10 myscript.sh
-rw-r--r--  1 nikhil nikhil    8832 2011-03-24 05:58 newname.tex
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-08 03:11 one-templates
d-wx--x--x  7 root   root      4096 2011-03-25 00:59 Ontologies
-rw-r--r--  1 nikhil nikhil   79192 2011-03-24 07:32 output!.png
-rw-r--r--  1 nikhil nikhil   74760 2011-03-24 07:28 output.png
-rwxr-xr-x  1 root   root   7793827 2011-03-25 00:59 owlapi-3.2.2.zip
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 01:07 Pictures
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 01:07 Public
-rw-r--r--  1 nikhil nikhil    1671 2011-03-19 02:47 SeWiki
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 02:25 Source
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 01:07 Templates
-rw-r--r--  1 nikhil nikhil   77802 2011-03-24 07:18 testcase1.png
-rw-r--r--  1 nikhil nikhil   86440 2011-03-24 07:19 testcase2.png
-rw-r--r--  1 nikhil nikhil   72886 2011-03-24 07:19 testcase3.png
drwxr-xr-x  2 nikhil nikhil    4096 2011-03-07 01:07 Videos
drwxr-xr-x  5 nikhil nikhil    4096 2011-03-19 16:06 workspace


```

also the line XDG_DESKTOP_DIR="$HOME/Desktop" exists in the specified folder

---

### Post by PCNetSpec on 2011-03-25
OK you don't have read permission for the Desktop directory.

Open a terminal and enter:

```
chmod 755 Desktop
```

and hit enter.

Remember Linux commands ARE case sensitive.

You *may* have to log off and on again.

---

