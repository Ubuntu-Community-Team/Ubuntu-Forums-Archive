---
title: "Unmet dependencies xlib-data"
date: 2006-05-07
forum: General Help
---

### Post by Mexxus on 2006-05-07
Hi there,

I'm currently installing my new ubuntu dapper system. During installing software with apt-get, i got a message like:

```
root@TRANSLTR:~# apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
                   Depends: make but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  xlibs: Depends: xlibs-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

It is continously farting about that xlibs thing. I really don't know what it means. Whet i try a "apt-get install -f", it says:

```
root@TRANSLTR:~# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xlibs-data
The following NEW packages will be installed:
  xlibs-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/860kB of archives.
After unpacking 7406kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 73492 files and directories currently installed.)
Unpacking xlibs-data (from .../xlibs-data_6.8.2-10.2_all.deb) ...
Replaced by files in installed package libx11-6 ...
dpkg: error processing /var/cache/apt/archives/xlibs-data_6.8.2-10.2_all.deb (--unpack):
 error creating directory `./usr/X11R6/lib/X11/locale/C': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xlibs-data_6.8.2-10.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think my xlibs thing is broken or something. I dont even know what xlibs is :(. Someone know how to fix this?

---

### Post by Ramses de Norre on 2006-05-07
Ignore this..

---

### Post by Mexxus on 2006-05-07
[QUOTE=Ramses de Norre]Ignore this..[/QUOTE]

Why ignore? I can't do anything :(

---

### Post by Ramses de Norre on 2006-05-07
No, no, I did a suggestion but it wouldn't help so I deleted it. But you can't delete a post..
I thought you ran the command without root permissions but I saw you were at a root terminal. Confusing ;)

---

### Post by Mexxus on 2006-05-07
Hmm.. someone else know what to do? I don't feel happy installing this whole thing over again...

---

