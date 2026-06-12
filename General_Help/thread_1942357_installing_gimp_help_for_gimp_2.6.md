---
title: "installing gimp help for gimp 2.6"
date: 2012-03-17
forum: General Help
---

### Post by Mickser_52 on 2012-03-17
I have been trying to install the latest gimp help with little sucess until this morning. I downloaded gimp-help-2.6.0-html-en.tar.bz2 and extracted gimp-help-2. In this was an "install" text file which said to copy files to $prefix/share/gimp/2.0/help, which turned out to be /usr/share/gimp/2.0/help. On opening /usr/share/gimp/2.0 there was no help folder. It did not say exactly which files to copy.

To make a long story (2 hours experimenting)short, the following worked:

from terminal.  1. sudo mkdir /usr/share/gimp/2.0 help

		2. in the extracted gimp-help-2 folder open the html folder and find the en folder (or whichever language you downloaded)

		3. This was then copied and pasted to the Desktop

		4. sudo mv /Desktop/en /usr/share/gimp/2.0/help

When I opened gimp and used the help with the web browser option it opened up.

Hope this may be of use

---

### Post by kazztan0325 on 2012-03-17
Hi Mickser_52,

I have no intention to dispute your way, but I think installing a package 'gimp-help-en' with Software Center or Synaptic Package Manager is much easier than your way.

Precisely, if we would open 'Language Support' which is in 'System Settings' after installing GIMP (or Thunderbird, LibreOffice), 'Language Support' would show us the lack of language pack(s) and help file(s) for application(s), and it ask us if it would install them now or later.
This way, we would be able to install language pack(s) and help file(s) for GIMP, Thunderbird and LibreOffice instead of installing them by our hands.

---

### Post by Mickser_52 on 2012-03-17
The problem was that the latest package in Software Center or Synaptic Package Manager is 2.4.

---

### Post by kazztan0325 on 2012-03-17
Oh, I'm sorry.
I should have asked you about the version of Ubuntu and GIMP which you are using.

---

