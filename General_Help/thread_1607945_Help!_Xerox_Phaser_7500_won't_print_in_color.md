---
title: "Help! Xerox Phaser 7500 won't print in color"
date: 2010-10-28
forum: General Help
---

### Post by dumb_question on 2010-10-28
I have a Xerox 7500 at work, color printing was working fine with 10.04. Had a bad upgrade and had to install 10.10 from scratch onto a new partition. Works fine except now after reinstalling the printer I can't get it to print color anymore, the only options under Properties / Device / Color model are "Grayscale" and "Inverted Grayscale".

Things I have already tried:

the automatic linux find-print-driver - this is how I got it set up originally - there is no 7500, but there are drivers for various 7400s and 7700s, tried both CUPS+Gutenprint & Foomatic/PostScript plus a few others - all give only the Grayscale / Inverted Grayscale options, a test page comes out grayscale, Print self-test page craps out with:

> CUPS server error
There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

Driver from Xerox
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=53867&EULA=0&prodID=7500&Family=Phaser&ripId=&langs=English%20%28N.%20America%29&plats=Linux&Xtype=download&uType=]("http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=53867&EULA=0&prodID=7500&Family=Phaser&ripId=&langs=English%20%28N.%20America%29&plats=Linux&Xtype=download&uType=") - when I try to run setup it gives me the EULA, I hit "y", and then it crashes out with:

> /usr/bin/lpq: Error - unknown destination "/tmp"!
................ERROR: No such file or directory

(and my /tmp exists, I checked) - this happens using sudo or sudo su

I then tried extracting the files and manually applying each of the 5 different .ppd files I found in there, (one generic xerox, 2 level 1 postscript and 2 level 2 postcript PPDs), but all of them left me with grayscale but no color.

It sees the printer fine, can display the ink / toner levels for all the colors etc etc etc, and prints nicely enough in grayscale, but I need color images for some work stuff I need to pass around shortly.

Any thoughts on what to do next?

---

### Post by psorcerer on 2010-10-31
Same problem with Xerox 6250DP
Opened bug: [https://bugs.launchpad.net/ubuntu/+bug/669152](https://bugs.launchpad.net/ubuntu/+bug/669152)

---

### Post by MatthiasAlbrecht on 2011-03-14
Ladies and Gentlemen,

being new to this forum, this is my first post. We had to install a brand new Xerox Phaser 7500 DX and ran into the same problem. After about two hours, I found  [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main-nonfree/binary-amd64/openprinting-ppds-postscript-xerox_20090512-4lsb3.2_all.deb](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main-nonfree/binary-amd64/openprinting-ppds-postscript-xerox_20090512-4lsb3.2_all.deb)

Download this, install it with 

"sudo dpkg -i [openprinting-ppds-postscript-xerox_20090512-4lsb3.2_all.deb" ]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main-nonfree/binary-amd64/openprinting-ppds-postscript-xerox_20090512-4lsb3.2_all.deb")

and create a new printer. Since the Xerox Phaser 7500 DX is not in the list, I chose Xerox Phaser 7400 DX. When it comes to the driver selection, you will find "Xerox Phaser 7400DX, Postscript-Xerox 20090512 (OpenPrinting LSB 3.2) (en)". Choose that one and thereafter you will be able to fully configure your printer including all options. Finish and you will be able to print in full color.

The Debian Packages named above has been supplied by Xerox to which I owe a lot.

[]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main-nonfree/binary-amd64/openprinting-ppds-postscript-xerox_20090512-4lsb3.2_all.deb")

---

