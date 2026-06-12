---
title: "Good and Simple XML Editor for Ubuntu 12.04"
date: 2012-05-05
forum: General Help
---

### Post by deepaknet on 2012-05-05
We have something called 'XML Notepad 2007' in Windows which facilitates editing XML files in a tree fashion.

Can some  one help out with an equivalent tool for Ubuntu 12.04 LTS?

---

### Post by dragonfly41 on 2012-05-05
**[COLOR=Gray]xmlcopyeditor[/COLOR]** found in in Synaptic Package Manager

---

### Post by deepaknet on 2012-05-05
Thank you. I installed it but the app does not seem to be starting up. Is there a way to find out if it is running into some issues? Will it log any errors somewhere?

I issued the following command to install

sudo apt-get install xmlcopyeditor

(~13 mega bytes)

---

### Post by dragonfly41 on 2012-05-05
run command **[COLOR=Gray]$ locate -e xmlcopyeditor[/COLOR]**

to see where files are installed

[p.s.]

If you install**[COLOR=Gray] Htop[/COLOR]** you can see running processes ..

my xmlcopyeditor is running as user root (on ubuntu 10.10 32 bit)

so you might try **[COLOR=Gray]$ gksudo xmlcopyeditor[/COLOR]**

to launch

---

### Post by deepaknet on 2012-05-05
lavanyadeepak@lavanyadeepak:~$ locate -e xmlcopyeditor
/usr/share/app-install/desktop/xmlcopyeditor:xmlcopyeditor.desktop
/usr/share/app-install/icons/xmlcopyeditor.png

---

### Post by dragonfly41 on 2012-05-05
Something is wrong since I have many more files installed ..

Can you try a direct download of the deb file ..

[http://sourceforge.net/projects/xml-copy-editor/files/xmlcopyeditor-linux/1.2.0.6/xmlcopyeditor_1.2.0.6-2_i386.deb/download](http://sourceforge.net/projects/xml-copy-editor/files/xmlcopyeditor-linux/1.2.0.6/xmlcopyeditor_1.2.0.6-2_i386.deb/download)

and install that way?

---

### Post by deepaknet on 2012-05-05
I tried the DEB file from the URL you suggested me and it complains of an unsatisfied dependency.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
you could try using [geany]("apt:geany") or [scite]("apt:scite")

edit:you may want the [tree browser addon]("apt:geany-plugin-treebrowser") for geany
maybe even one of or more of these addons (tools -> plugins manager to activate them)
[XML Snippets]("apt:geany-plugin-xmlsnippets")
[XML Pretty Printer]("apt:geany-plugin-prettyprinter")

---

### Post by deepaknet on 2012-05-05
Wonderful. I in fact use Geany. Let me try and get that Tree Addon.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
you can find a lot of useful things by typing a apps name in synaptic
infant i found a couple i could use myself :)

---

### Post by deepaknet on 2012-05-05
I did have a look at the Synaptic but some have abysmally greater dependencies and/or higher sizes. Hence I preferred to take the advise of experts.

The Geany thing seems to be promising. Let me have a look at it tonight.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
i just found out about its addons because of this thread :)
i really needed the spell checker i had been open files up in gedit for that for over a year

---

### Post by dragonfly41 on 2012-05-06
You may already have another xml editor working by now such as Geany | Scite but just to explain the error you had with xmlcopyeditor

> I tried the DEB file from the URL you suggested me and it complains of an unsatisfied dependency.

It may be that you don't have the correct libxerces version installed .. libxerces is the xml parser library.   

This old thread explains the dependency issue

[http://ubuntuforums.org/archive/index.php/t-1640003.html](http://ubuntuforums.org/archive/index.php/t-1640003.html)

I think you will have to look here for archived libraries for 12.04 ..

[http://packages.ubuntu.com/precise/](http://packages.ubuntu.com/precise/)

and here it is ..

[http://packages.ubuntu.com/precise/libxerces-c3.1](http://packages.ubuntu.com/precise/libxerces-c3.1)

Being curious I inspected the *.deb dependencies using a useful bash script I found some time ago when I had dependency issues on a package .. 

[http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/](http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/)

This is what I found from inspecting xmlcopyeditor (using above bash script placed in ~/bash_scripts/)

gksudo ~/bash_scripts/edit-deb-control.sh ~/bash_scripts/xmlcopyeditor_1.2.0.6-2_i386.deb

```

Package: xmlcopyeditor
Priority: extra
Section: checkinstall
Installed-Size: 10068
Maintainer: Gerald Schmidt <gnschmidt@users.sourceforge.net>
Architecture: i386
Version: 1.2.0.6-2
Depends: libexpat1,libxslt1.1,libxml2,libpcre3,libxerces-c3.0,libwxgtk2.8-0
Provides: xmlcopyeditor
Description: XML editor

```

And here is the bash script I use .. note that if you edit the dependencies a modified *.deb package is created.

[COLOR="Blue"]Script from here ..

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)[/COLOR]

```

#!/bin/bash

EDITOR=gedit

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
OUTPUT=`basename "$DEBFILE" .deb`.modified.deb

if [[ -e "$OUTPUT" ]]; then
  echo "$OUTPUT exists."
  rm -r "$TMPDIR"
  exit 1
fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
$EDITOR "$CONTROL"

if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modified.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"

```

---

