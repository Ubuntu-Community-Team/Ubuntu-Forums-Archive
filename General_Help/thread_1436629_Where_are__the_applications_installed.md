---
title: "Where are  the applications installed?"
date: 2010-03-22
forum: General Help
---

### Post by rva1945 on 2010-03-22
Yes, that's a common question from us (ex-) Windows users. For example: I'd like to use some of the (wav?) sound files heard in the Xboing blocks game. How do I access its folder?

I guess there's a Terminal command that gives me that info, as sure it can be accessed via some of the graphic interfaces.

Thanks

---

### Post by Dantevus on 2010-03-22
What is your Distro and are you using Gnome or KDE?

---

### Post by ScarletWyvern on 2010-03-22
To my knowledge, the application itself (i.e. the executable) is stored in one of the several bin directories, but the files that applications use are generally stored somewhere in the /usr folder.

Root around in there and you might be able to find something.

---

### Post by darolu on 2010-03-22
Take a look at this link: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

For more indepth information, open a Terminal (applications - accessories - terminal) and type this (press Q to quit):
```
$ man hier
```

They are usually installed at */bin directories (binaries that is), some elements can be installed elsewhere, programs installed via package manager (the normal way) are installed in regular $PATH directories, to learn what directories are in your PATH type this in your terminal:
```
$ echo $PATH
```
Then you can browse through this directories, you will find with many [symbolic links]("http://en.wikipedia.org/wiki/Symbolic_link") (kinda like windows shortcuts) to find where they point to, type:
```
$ ls -l <symlink>
```
for example:
```
/usr/bin$ ls -l firefox
lrwxrwxrwx 1 root root 31 2010-02-18 15:27 firefox -> ../lib/firefox-3.5.8/firefox.sh
```

---

### Post by gadolinio on 2010-03-23
> **rva1945 said:**
> Yes, that's a common question from us (ex-) Windows users. For example: I'd like to use some of the (wav?) sound files heard in the Xboing blocks game. How do I access its folder?

I guess there's a Terminal command that gives me that info, as sure it can be accessed via some of the graphic interfaces.

Thanks

Maybe the command "whereis APPLICATION_NAME" can help you. It gives you the locations of the app's files. Then you can search in there to find what you want. If there are too many subdirectories, go to places--> search, and look for the filetype you expect (do searches for wav, mp3, etc) inside the folders given by whereis.

---

### Post by srs5694 on 2010-03-23
In Linux, an individual application's files are often installed in several different directories. For instance, the program binary may be in /usr/bin, its configuration files in /etc, icons in /usr/share/icons, and so on. For your specific goal, your best bet is to use the Debian package management system to locate the files installed from the package using the package database. If you know the package name, you can do this from the command line using dpkg and its -L option:

```

dpkg -L xboing

```

The result should be a list of files and directories. Sometimes this list is very long, so you may need to scroll back through it, pipe it into less, or use grep to search for files in specific subdirectories or with certain filename extensions, as in:

```

dpkg -L xboing | less
dpkg -L xboing | grep png

```

The first example uses the less pager to view the results, and the latter searches for files with "png" extensions (or "png" anywhere in the filename, really). (I don't happen to have this package installed on my system, so I don't know if it actually contains any .png files.)

If you don't know the package name but do know the filename of any file in the program (determined via whereis, as gadolinio suggests), you can use the -S option to dpkg to locate a package name from a filename, as in:

```

dpkg -S /bin/bash 
bash: /bin/bash

```

This reveals that the package to which /bin/bash belongs is called "bash". You can then search for other files in this package by using -L ("dpkg -L bash").

If you prefer a GUI, the Synaptic package manager lets you do most of these things. You can search for a package by name, then right-click it and select "Properties." In the resulting dialog box, there's an "Installed Files" tab that shows the installed files.

---

