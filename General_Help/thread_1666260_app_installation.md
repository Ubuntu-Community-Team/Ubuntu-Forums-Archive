---
title: "app installation ?"
date: 2011-01-13
forum: General Help
---

### Post by Pedroparamo on 2011-01-13
I'm trying to install and app using

 [FONT=Courier New]sudo aptitude install ghostscript[/FONT]

but the command line returns the following message:

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 211 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Does this mean it' already installed?  Why doesn't it just say that?

Thanks.

Pedro

---

### Post by Smart Viking on 2011-01-13
Yes it is most likely installed.

To be sure:
```
(smartviking)-(jobs:0)-(~/tem)
(! 569)-> sudo aptitude search ghostscript
i   ghostscript                                                                         - The GPL Ghostscript PostScript/PDF interpreter                                               
i   ghostscript-cups                                                                    - The GPL Ghostscript PostScript/PDF interpreter - CUPS filters                                
p   ghostscript-doc                                                                     - The GPL Ghostscript PostScript/PDF interpreter - Documentation                               
i   ghostscript-x                                                                       - The GPL Ghostscript PostScript/PDF interpreter - X Display support                           
```
The packages that are installed have an "i" on front of them, as you can see, on my system it is installed.

---

### Post by Ad@m on 2011-01-13
sudo aptitude show ghostscript

That will indicate if it is installed.

EDIT: or as above :)

---

### Post by weedeater64 on 2011-01-13
Yeah, Looks like it is already installed.

You can see everything that is installed with 

```
dpkg --get-selections
```

that will output a lot of info, that will probably run off of the buffer, so you should pipe it through less,

```
dpkg --get-selections | less
```

which which will allow you to peruse the output, 

do 

```
man less
```

to see how that works..

Alternatively you could redirect the output into a text file,

```
dpkg --get-selections > you-choose-filename.txt
```

You can then open that file with gedit and look at it..

---

### Post by Pedroparamo on 2011-01-13
I guess it is installed--I get the following when I run 

sudo aptitude show ghostscript


Package: ghostscript                     
State: installed
Automatically installed: no
Version: 8.71.dfsg.2-0ubuntu7
Priority: optional
Section: text
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 10.3M
Depends: libc6 (>= 2.0), libgs8 (= 8.71.dfsg.2-0ubuntu7), gsfonts (>=
         1:8.11+urwcyr1.0.7~pre44-4.1), debconf | debconf-2.0, debianutils (>=
         1.6)
Suggests: ghostscript-cups, ghostscript-x, hpijs
Conflicts: ghostscript-fonts, gs (< 8.63), gs-afpl (< 8.63), gs-aladdin (<
           8.63), gs-cjk-resource (< 1.20010910-1), gs-common (< 8.63), gs-esp
           (< 8.63), gs-gpl (< 8.63), gs-pdfencrypt (< 7.00)
Replaces: ghostscript-fonts, gs (< 8.63), gs-afpl (< 8.63), gs-aladdin (< 8.63),
          gs-common (< 8.63), gs-esp (< 8.63), gs-gpl (< 8.63), gs-pdfencrypt (<
          7.00)
Provides: gs-common, gs-pdfencrypt, postscript-viewer
Description: The GPL Ghostscript PostScript/PDF interpreter
 Ghostscript is used for PostScript/PDF preview and printing.  Usually as a
 back-end to a program such as ghostview, it can display PostScript and PDF
 documents in an X11 environment. 
 
 Furthermore, it can render PostScript and PDF files as graphics to be printed
 on non-PostScript printers. Supported printers include common dot-matrix,
 inkjet and laser models. 
 
 Package gsfonts contains a set of standard fonts for Ghostscript.
Homepage: [http://www.ghostscript.com/](http://www.ghostscript.com/)


Why does it indicate  'Automatically installed: no'--what does that mean?

Thanks.

Pedro

---

### Post by Smart Viking on 2011-01-15
> **Pedroparamo said:**
> 
Why does it indicate  'Automatically installed: no'--what does that mean?

Thanks.

Pedro
That means that is weren't automatically installed to the system, like as a dependency or something but that you the user installed it.

---

