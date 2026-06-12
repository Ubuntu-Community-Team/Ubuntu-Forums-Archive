---
title: "purging a broken package"
date: 2011-10-11
forum: General Help
---

### Post by prunyboy on 2011-10-11
hey all
so i was installing ubuntu studio onto my regular ubuntu 10.10 setup, but it was interrupted halfway through by a power cut. i tried to reinstall but had no joy :/ it would always stop at installing tex-common and all the packages dependent on it because it could not find some missing configuration files.

i then tried to purge tex-common using 'apt-get purge tex-common' which then made it hang and reboot when it started searching for the missing configuration files. 

i found the supposedly missing configuration files in /etc myself and deleted them (rookie error i know) and now when i try to purge or install tex-common it hangs and reboots. 

please help, i have no idea how to solve this :(

---

### Post by ajgreeny on 2011-10-11
Try using **synaptic ->Edit ->Fix Broken Packages** which can sometimes work when other methods fail.

---

### Post by prunyboy on 2011-10-12
no luck from that either.

also, when i ran sudo dpgk --configure -a it gave this error:


colin@rednblack:~$ sudo dpkg --configure -a
Setting up tex-common (2.08ubuntu0.1) ...
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
egrep: /etc/texmf/texmf.d/55Fonts.cnf: No such file or directory
Error in /etc/texmf/texmf.d/55Fonts.cnf: TEXFONTMAPS not defined.
Error in /etc/texmf/texmf.cnf: TEXFONTMAPS not defined.
Unrecoverable errors in your configuration have been detected
in configuration files in /etc/texmf/.
If you've not seen debconf error messages,  see your mail for details
or use an interactive debconf frontend.

Exiting
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common




any ideas?

---

### Post by ajgreeny on 2011-10-12
Sorry, but no ideas at all.

---

