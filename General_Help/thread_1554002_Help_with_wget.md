---
title: "Help with wget"
date: 2010-08-16
forum: General Help
---

### Post by elliotn on 2010-08-16
Please help.
What I want to do is I want to use wget to download parkages at parkages.ubuntu.com using a Windows Xp computer that has internet.

All I want is someone to help with a Script that will run in windows and would download parkages with its dependencies.

Example. Lets say I want vlc. The wget script should be able to download all dependencies(vlc-nox, libavuti52 etc)
Is it possible?

---

### Post by elliotn on 2010-08-23
Bump,

---

### Post by elliotn on 2010-08-23
Ok and I have the addreses to da dependencies but want to download em all at once

---

### Post by surfer on 2010-08-23
google suggests [this]("http://www.tuxradar.com/answers/517").

any help?

---

### Post by elliotn on 2010-08-23
> There are at least two ways
to do this. The quick and
easy option is to use the
'Generate package download
script' option in Synaptic. Mark
the packages you want to install,
then select this option from the
File menu, which will generate a
shell script that you can run to
download the packages. Then
you transfer the packages to
your Ubuntu box and either put
them in /var/cache/apt/archives
or use the 'Add downloaded
packages' menu option in
Synaptic to install them. The
main disadvantage of this
method is that the script requires
wget, so you need this installed
on the computer you use for the
downloading. An alternative is to
use apt-get from the command
line with the --print-uris option.
Apt-get will automatically try to
install all dependencies, and the
--print-uris option outputs the
URIs of all the files it needs. You
can use grep and cut to extract
the URIs from the output with
a p t - g e t - - p r i n t - u r i s - - y e s i n s t a l l pk g s pe c | g r e p ^ \ ' | c u t - d\ ' - f 2 > do w n l oa d s . l i s t
For example, running this with
'postgrey' instead of the word
'pkgspec' creates a file
containing
h t t p : / / s e c u r i t y . ubun t u . c o m / ubun t u / poo l / un i v e r s e / l i bn / l i bne t - dn s - pe r l / l i bne t - dn s - pe r l _ 0 . 5 9 - 1 bu i l d1 . 1 _ i 3 8 6 . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l / un i v e r s e / l i bb / l i bbe r k e l e y db - pe r l / l i bbe r k e l e y db - pe r l _ 0 . 3 1 - 1 _ i 3 8 6 . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l /m a i n / l i bd / l i bd i g e s t - s ha 1 - pe r l / l i bd i g e s t - s ha 1 - pe r l _ 2 . 1 1 - 1 bu i l d1 _ i 3 8 6 . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l /m a i n / l i bd / l i bd i g e s t - h m a c - pe r l - d f s g / l i bd i g e s t - h m a c - pe r l _ 1 . 0 1 - 5 _ a l l . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l / un i v e r s e / l i b i / l i b i o -m u l t i p l e x - pe r l / l i b i o -m u l t i p l e x - pe r l _ 1 . 0 8 - 3 _ a l l . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l / un i v e r s e / l i bn / l i bne t - c i d r - pe r l / l i bne t - c i d r - pe r l _ 0 . 1 1 - 1 _ a l l . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l / un i v e r s e / l i bn / l i bne t - i p - pe r l / l i bne t - i p - pe r l _ 1 . 2 5 - 2 _ a l l . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l / un i v e r s e / l i bn / l i bne t - s e r v e r - pe r l / l i bne t - s e r v e r - pe r l _ 0 . 9 4 - 1 _ a l l . de b
h t t p : / / g b . a r c h i v e . ubun t u . c o m / ubun t u / poo l / un i v e r s e / p / po s t g r e y / po s t g r e y _ 1 . 2 7 - 4 _ a l l . de b
As you can see, this includes the
dependencies as well as the
program itself. Copy
download.list to a USB flash
drive to take it to the computer
with the faster internet
connection. Many FTP programs
and download managers will
read a list of download URLs
from a file, such as
w g e t - - i npu t - f i l e m y u r i l i s t
You can give more than one
package name as 'pkgspec'
However, you do need to run
the apt-get update from time to
time to keep up to date. If you
are using another connection
because your home computer is
on a slow dial-up, there's no
problem, as apt-get update
doesn't download much. If you
have no internet access at all,
you can run apt-get --print-uris
update and download the files
elsewhere, then copy, unpack
and rename the Sources files in /
var/lib/apt/lists.


My problem is setting a wget scripts to put the url's to download all the required parkages to my flash drive.

I know how to get the url via SYNAPTIC.

---

### Post by surfer on 2010-08-23
example for emacs22:

```
apt-get --print-uris --yes install emacs22 | grep ^\' | cut -d\' -f2
```

gives

```

http://archive.ubuntu.com/ubuntu/pool/universe/e/emacs22/emacs22-common_22.2-0ubuntu9_all.deb
http://archive.ubuntu.com/ubuntu/pool/universe/e/emacs22/emacs22-bin-common_22.2-0ubuntu9_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-17build1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/universe/e/emacs22/emacs22_22.2-0ubuntu9_i386.deb

```

when in write that in a file (named download.list), i can
```
$ wget --input-file download.list

```

---

### Post by elliotn on 2010-08-23
> **surfer said:**
> example for emacs22:

```
apt-get --print-uris --yes install emacs22 | grep ^\' | cut -d\' -f2
```

gives

```

http://archive.ubuntu.com/ubuntu/pool/universe/e/emacs22/emacs22-common_22.2-0ubuntu9_all.deb
http://archive.ubuntu.com/ubuntu/pool/universe/e/emacs22/emacs22-bin-common_22.2-0ubuntu9_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-17build1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/universe/e/emacs22/emacs22_22.2-0ubuntu9_i386.deb

```

when in write that in a file (named download.list), i can
```
$ wget --input-file download.list

```
Then how do I make wget download straight to my flash drive

---

### Post by J V on 2010-08-23
So far every answer seems to be around bash scripts and/or wget...

Use kreyx: It lets you mark packages and updates on a usb stick then take it to a windows machine downloads them automatically and puts them on the ubuntu machine...

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by surfer on 2010-08-23
didn't know about [http://keryxproject.org/](http://keryxproject.org/). looks nice! thanks!

---

