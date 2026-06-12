---
title: "ubuntu 11.0 dosbox does not print lpt"
date: 2012-02-21
forum: General Help
---

### Post by aasha on 2012-02-21
I have installed ubuntu 11., **[COLOR=#ff0000]dosbox[/COLOR]** .
I need to execute foxpro programs. It works fine for entry.
But it cannot print lpt printer.
 
Dosemu prints on lpt printer. But it crashes for entry.
 
 
Kindly advise

---

### Post by mips on 2012-02-21
Dosbox dos not have LPT support out of the box. If you want LPT support you must compile one of the enhanced builds from source.

[http://www.dosbox.com/wiki/SVN_Builds](http://www.dosbox.com/wiki/SVN_Builds)
Have a look at ykhwong, "Mega Build" series (by H-A-L-9000) & "UBER BUILD" (by Virusek)

For more info on dosbox builds have a look at the forums [http://vogons.zetafleet.com/viewforum.php?f=32](http://vogons.zetafleet.com/viewforum.php?f=32)

Another option to look at would be VMware Player or Server which are free and has LPT support from what I have read before.

---

### Post by paul1945 on 2012-07-22
I have Ubuntu 12.04 and have the same problem with DosBox. Tried Dosemu,  but that will print from the command line but not pipe print  information from a program. 
For now I have the program writing the print output to a ".PRN" file and  made a DosPrint.sh file that sends the file to a network printer as a  printer file, as follows:

DosPrint.sh
=====================================================
#!/bin/bash
lpr -P HP-LaserJet-m2727-MFP -l -r /home/paul/dosdrive/*.PRN
=====================================================

It works and ".RAW" files can be printed in the same way.
Unfortunately this is not an elegant solution, as you have to exit  DosBox and click on the link to have the file printed. I have tried one  of the Dosbox SVN builds (from ykhwong) on a Windows XP machine, and it  prints perfectly on that; so we need someone with a bit of knowhow (and  goodwill) to compile a SVN Build version for Ubuntu.

---

### Post by paul1945 on 2012-07-22
Message was accidentally saved twice, cannot see how to delete this

---

### Post by paul1945 on 2012-10-19
Have managed to compile a version with some help of Dosbox SVN version that prints, also with dBase 5, and can even be made to print over a network. If anyone needs it.

---

