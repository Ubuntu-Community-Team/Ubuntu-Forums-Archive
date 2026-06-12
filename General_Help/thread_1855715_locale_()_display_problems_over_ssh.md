---
title: "locale (?) display problems over ssh"
date: 2011-10-06
forum: General Help
---

### Post by flangemonkey on 2011-10-06
Hi,

I run Gentoo on my laptop and Xubuntu on one of my servers; when I log in over SSH aspects of my terminal fail to display correctly

Here is a screenshot of alsamixer failing to display correctly
[tinypic screenshot link]("http://tinypic.com/r/de9x5e/7")

another associated error I think will be relevant, is similar to those posted by others:

```

**on opening a man page:**

man: can't set the locale; make sure $LC_* and $LANG are correct

```

locale details for both machines

```

ubuntu# locale
LANG=en_GB.UTF-8
LANGUAGE=
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE=C
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

```

```

gentoo# locale
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```

I have run

```

export LC_ALL="POSIX"
apt-get install locales
dpkg-reconfigure locales
apt-cache policy language-pack-en
locale-gen POSIX
dpkg-reconfigure libncurses5 (no output)
dpkg-reconfigure ncurses-base (no output)
dpkg-reconfigure ncurses-bin (no output)
reset (better; but like this screenshot: [HERE]("http://tinypic.com/r/16lbmzp/7")

``` on the ubuntu server (same)

and 

```

export LC_ALL="en_GB.utf8"

``` on the gentoo laptop (same)

Interestingly ssh from gentoo laptop to ubuntu server and then to another gentoo server yields the same problem with display, but ssh directly to gentoo server doesn't.

it should be noted that the install has been like this since xubuntu 7.10, and I've just upgraded between the releases to 11.04.

alsamixer runs and displays fine locally on the xubuntu server.

---

### Post by flangemonkey on 2011-10-08
turns out it is Gentoo not displaying UTF-8 correctly in a posix environment; I'll post in the forums there and post back the solution, should it be isolated :)

---

### Post by flangemonkey on 2011-10-09
At the moment I'm not very parfait with how locales work, but to work around this issue adding 

```

export LC_CTYPE="en_GB-UTF-8" 

```
to your bashrc file ( */etc/bash/bashrc (systemwide)* or *~/.bashrc (per user) )* or your overall profile (for other shells) will set the _active_ locale to UTF-8 on all _new_ logins.

and everything will display perfectly ;)

FM

---

