---
title: "The tangled web of Unix folders"
date: 2006-06-16
forum: General Help
---

### Post by RJMacReady on 2006-06-16
Can anyone please post describing what all the folders in a Unix system are for?

Eg: Bin, etc, dev...

Or, failing that, are there any guides online which detail what they're for?

Thanks

RJ

---

### Post by juicybananahead on 2006-06-16
(Copied and pasted from [http://www.debian.org/doc/manuals/user/ch-files.html](http://www.debian.org/doc/manuals/user/ch-files.html))

/
    ...this is the root directory, which contains every other directory. 

/root
    But don't get / confused with /root! /root is the home directory of the root user, or superuser. It's a directory called /root, but it isn't the root directory /. 

/home
    This is where all normal users - that is, all users except root - have their home directories. Home directories are named after the user who owns them. If you're using a large system at a school or business, your system administrator may create additional directories to contain home directories: /home1 and /home2 for example.

    Your home directory is where you put all your personal work, email and other information, and personal configuration preferences. 

/bin
    This directory contains "binaries," executable files which are essential to the operation of the system. Examples are: the shell (bash), and the commands you just learned such as cp. 

/sbin
    This directory contains "system binaries," things that the root user or system administrator might want to use, but probably you won't want to use in your day-to-day activities. 

/usr
    /usr contains most of the files you'll be interested in. It has many subdirectories: /usr/bin and /usr/sbin are pretty much like /bin and /sbin, except that the directories in /usr are not considered "essential to the operation of the system."

    While not essential to get the computer operating,/usr does contain the applications you'll use to get real work done. Also in /usr you'll find the /usr/man, /usr/info, and /usr/doc directories - these contain manual pages, info pages, and other documentation, respectively. And don't forget /usr/games! 

/usr/local
    The Debian system doesn't install anything in this directory. You should use it if you want to install software that you compile yourself, or any software not contained in a Debian package. You can also install software in your home directory, if you'll be the only one using it. 

/etc
    /etc contains all the system-wide configuration files. Whenever you want to change something that affects all users of your computer - such as how you connect to the internet, or what kind of video card you have - you'll probably have to log on as root and change a file in /etc. 

/tmp
    Here you'll find temporary files, most of them created by the system. This directory is generally erased on a regular basis, or every time you reboot the system. You can create files here if you want, just be aware they might get deleted automatically. 

/var
    /var contains "variable" files, that the system changes automatically. For example, incoming mail is stored here. The system keeps a log of its actions here. There are a number of other automatically generated files here as well. You'll mostly be interested in the contents of /var/log, where you can find error messages and try to figure out what you're system's up to if something goes wrong. 

Clearly there are many more directories on the system, too many to describe every one. We'll get to some of them later in the manual.

For changing things, you'll usually want to confine yourself to your home directory and /etc. On a Debian system, there's rarely an occasion to change anything else, because everything else is automatically installed for you.

/etc is used to configure the system as a whole. You'll use your own home directory, a subdirectory of /home, for configuring your own preferences, and storing your personal data. The idea is that on a day-to-day basis you confine yourself to /home/yourname, so there's no way you can break anything. Occasionally you log in as root to change something in a system-wide directory, but only when absolutely necessary. Of course, if you're using Debian at a school or business and someone else is the system administrator, you won't have root access and will only be able to change your home directory.

---

### Post by soonindallas on 2006-06-16
there is indeed an standard.  try reading this: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by RJMacReady on 2006-06-16
Thanks for that!

Wow, thats a lot of folders with a lot of uses. 

Methinks someone needs to unify a simpler Unix directory tree :P

---

### Post by glinsvad on 2006-06-16
The official Ubuntu desktop guide covers this:
[http://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html]("http://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html")

---

### Post by juicybananahead on 2006-06-16
I think that this graphic is based on Red Hat, but there should still be an awful lot common to both RH and Ubuntu.

[IMG]http://www.secguru.com/files/linux_file_structure.jpg[/IMG]

---

