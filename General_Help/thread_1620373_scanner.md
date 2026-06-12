---
title: "scanner"
date: 2010-11-13
forum: General Help
---

### Post by choochoousmc on 2010-11-13
asking again as no answers before.
Unbuntu 10.10
Epson all in one printer / scanner N X515  wireless

Ubuntu will print wirelessly.
But none of the scan programs will scan wirelessly

They all send a signal to scanner, but won't actually scan

Is there a cure / fix / work around?

TIA

---

### Post by sisco311 on 2010-11-13
Did you try iscan? [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

For 32-bit Ubuntu you need:
[list]
[*]iscan-data_1.4.0-1_all.deb
[*]iscan_2.26.0-3.ltdl7_i386.deb
[*]iscan-network-nt_1.1.0-2_i386.deb
[/list]

For 64-bit:
[list]
[*]iscan-data_1.4.0-1_all.deb
[*]iscan_2.26.0-3.ltdl7_amd64.deb
[*]iscan-network-nt_1.1.0-2_amd64.deb
[/list]

Direct links:
[http://linux.avasys.jp/drivers/iscan-data/1.4.0/](http://linux.avasys.jp/drivers/iscan-data/1.4.0/)
[http://linux.avasys.jp/drivers/iscan/2.26.0/](http://linux.avasys.jp/drivers/iscan/2.26.0/)
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/)

---

### Post by choochoousmc on 2010-11-13
> **sisco311 said:**
> Did you try iscan? [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

For 32-bit Ubuntu you need:
[LIST]
[*]iscan-data_1.4.0-1_all.deb
[*]iscan_2.26.0-3.ltdl7_i386.deb
[*]iscan-network-nt_1.1.0-2_i386.deb
[/LIST]

For 64-bit:
[LIST]
[*]iscan-data_1.4.0-1_all.deb
[*]iscan_2.26.0-3.ltdl7_amd64.deb
[*]iscan-network-nt_1.1.0-2_amd64.deb
[/LIST]

Direct links:
[http://linux.avasys.jp/drivers/iscan-data/1.4.0/](http://linux.avasys.jp/drivers/iscan-data/1.4.0/)
[http://linux.avasys.jp/drivers/iscan/2.26.0/](http://linux.avasys.jp/drivers/iscan/2.26.0/)
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/)

No I have not. And you raised a question.
How do I find out if I have 32 or 64 bit Ubuntu. The help doesn't say.
Also when I go to the web to download the files, is there a specific place I should save them to?
Is there a specific process for installing them, I'm newbie to way Linux does somethings.

---

### Post by sisco311 on 2010-11-13
> **choochoousmc said:**
> No I have not. And you raised a question.
How do I find out if I have 32 or 64 bit Ubuntu. The help doesn't say.


Open a terminal (Applications -> Accessories -> Terminal) and run:
```
uname -m
```
If the output is i386, i486, i586 or i686, then it's 32-bit. x86_64 means 64-bit.

> **choochoousmc said:**
> 
Also when I go to the web to download the files, is there a specific place I should save them to?


You can save them anywhere. After installation you can delete them, if you wish.

> **choochoousmc said:**
> 
Is there a specific process for installing them, I'm newbie to way Linux does somethings.

Double click.

---

### Post by choochoousmc on 2010-11-13
> **sisco311 said:**
> Open a terminal (Applications -> Accessories -> Terminal) and run:
```
uname -m
```If the output is i386, i486, i586 or i686, then it's 32-bit. x86_64 means 64-bit.



You can save them anywhere. After installation you can delete them, if you wish.



Double click.

Ok It came back with i686 so I have 32 bit version. would of been easier if they had just put this in in the ABOUT Ubuntu submenu.
I also read in the Meerkat issues / work arounds about the scanner with epson 640.
will try that also.
thanks for the help.

---

### Post by choochoousmc on 2010-11-21
ok, once again thanks.
But not quite ready to mark as solved as some question remain, hope you or someone can answer.
the installation added a image scan! for Linux to the graphics menu but won't run
Error: could not send command to scanner. Check scanner.
The installation added  Scanner utility also.
It works and does scan. However, I can only output to a PNG file format.
And in higher resolution does not fully scan entire document (may need to play with settings)
I tried to convert to jpeg with a photo viewer / editor.
Said I don't have permission.
so question how can I output to different format (I was scanning a text doc, in lineart)
How do I get permission to convert.

Xsane is still in the menu but will not activate and run.
simple scan says no scanner is detected
Can I uninstall these with out affecting the working scanner utility program that does work?

---

### Post by choochoousmc on 2010-11-22
solved kind of.
My scanner does work now.
But have to manually turn it off, to reset so printer will work right.
But only have one option for saving   .png  format.
a photo editor won't let me convert format, says I don't have permission.
even though I am the administrator

other Ubuntu scanner software still doesn't work though.

---

