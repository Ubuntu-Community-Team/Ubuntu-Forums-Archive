---
title: "MozPlugger LibreOffice Integration"
date: 2011-01-26
forum: General Help
---

### Post by texaswriter on 2011-01-26
Hi, 

I recently uninstalled Open Office and installed Libre Office. Love it!!

But, now the MozPlugger plugin in Firefox is not loading documents and such that are embedded in websites... 

Before I waste a bunch of time searching through dozens of folders and countless more files, what is the easiest way to fix this issue. 

Thanks in advance.

Well, looked into the file and was able to figure it out. Here is a before and after snapshot of a section of the mozpluggerrc file. 

This is the original section of the mozpluggerrc file in /etc
Had to use gksudo gedit /etc/mozpluggerrc

> ### OpenOffice
define([OO],[swallow(VCLSalFrame) fill: ooffice2.0 -nologo -norestore -view $1 "$file"
    swallow(VCLSalFrame) fill: ooffice -nologo -norestore -view $1 "$file"
    swallow(VCLSalFrame) fill: soffice -nologo $1 "$file"])
 Changed to: 

> 
### OpenOffice
define([OO],[swallow(VCLSalFrame) fill: libreoffice -nologo -norestore -view $1 "$file"
    swallow(VCLSalFrame) fill: libreoffice -nologo -norestore -view $1 "$file"
    swallow(VCLSalFrame) fill: libreoffice -nologo $1 "$file"])



---

