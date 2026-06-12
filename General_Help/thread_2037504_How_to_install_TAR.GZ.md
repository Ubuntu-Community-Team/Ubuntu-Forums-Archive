---
title: "How to install TAR.GZ?"
date: 2012-08-04
forum: General Help
---

### Post by DPM410 on 2012-08-04
I have tried installing OpenOffice (yes I know there is LibreOffice already installed) and it is a tar.gz file. How do I install it? I have tried extracting it to the downloads folder and it is exactly the same as it once was. How do I install any tar.gz file?

---

### Post by Paqman on 2012-08-04
Generally, you don't. A .tar.gz is just a compressed archive, and could contain anything. It could contain a proper .deb package, or a pre-compiled app that will just run (but doesn't install through your package manager), or it could contain a big mess of spaghetti that you have to compile yourself. There's no consistency, which is why I'd advise that you avoid them like the plague, as they can clog up your system with crud. You've got an amazing package manager built into your system, it's the main thing that sets Linux above Windows and OS X, so use it.

The [download page for OpenOffice]("http://www.openoffice.org/download/other.html") has .deb files available for 32- and 64-bit for Ubuntu.

---

### Post by vexorian on 2012-08-04
Please note that LibreOffice and OpenOffice are basically the same thing. Except that LibreOffice has a non-ugly logo and a license that puts users over corporations. Not only is it unnecessary for you to install the tar.gz, you do not need openOffice at all.

When the package is of an app that is well known like OpenOffice, then you would *rarely* need the tar.gz file. Instead look for a ppa or the .deb file.

As a rule of thumb though, next time you look for a program, and you cannot find a ppa nor a .deb package, then you might have to use the tar.gz file. My suggestion is to use the file manager to right click the file and decompress. Then there is almost always a file called INSTALL that contains some instructions. Get ready to have to install dependencies manually and compile using the command line.

---

### Post by DPM410 on 2012-08-04
Okay, thank you!

---

