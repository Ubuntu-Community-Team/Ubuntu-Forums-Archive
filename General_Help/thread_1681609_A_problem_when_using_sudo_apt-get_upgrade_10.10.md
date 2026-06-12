---
title: "A problem when using sudo apt-get upgrade 10.10"
date: 2011-02-04
forum: General Help
---

### Post by SkyHookers on 2011-02-04
```
linux@ubuntu:~$ sudo apt-get upgrade
[sudo] password for linux: 
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 0 ikke oppgradert.
10 pakker ikke fullt installert eller fjernet.
Etter denne operasjonen vil 0B ekstra diskplass bli brukt.
Vil du fortsette [Y/n]? y
Setter opp gnome-colors-common (5.5.1-1) ...
update-alternatives: error: cannot stat /lib/plymouth/themes/initrd.img-2.6.35-25-generic-pae/initrd.img-2.6: Ikke en filkatalog
dpkg: Feil ved behandling av gnome-colors-common (--configure):
 underprosessen installerte post-installation skript returnerte feilstatus 2
dpkg: Kravproblem hindrer oppsettet av gnome-brave-icon-theme:
 gnome-brave-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-brave-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-dust-icon-theme:
 gnome-dust-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-dust-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-human-icon-theme:
 gnome-human-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-human-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-illustrious-icon-theme:
 gnome-illustrious-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.Ingen apport-rapport skrevet fordi feilmeldingen indikerer at den er en følgefeil fra en tidligere feil.
                                                                          Ingen apport-rapport skrevet fordi feilmeldingen indikerer at den er en følgefeil fra en tidligere feil.
                  Ingen apport-rapport skrevet for MaxReports allerede er nådd
                                                                              Ingen apport-rapport skrevet for MaxReports allerede er nådd
                                                          Ingen apport-rapport skrevet for MaxReports allerede er nådd
                                      Ingen apport-rapport skrevet for MaxReports allerede er nådd
                  Ingen apport-rapport skrevet for MaxReports allerede er nådd
                                                                              Ingen apport-rapport skrevet for MaxReports allerede er nådd

dpkg: Feil ved behandling av gnome-illustrious-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-noble-icon-theme:
 gnome-noble-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-noble-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-wine-icon-theme:
 gnome-wine-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-wine-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-wise-icon-theme:
 gnome-wise-icon-theme krever gnome-colors-common. Men:
  Pakke gnome-colors-common er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-wise-icon-theme (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av gnome-colors:
 gnome-colors krever gnome-brave-icon-theme. Men:
  Pakke gnome-brave-icon-theme er ikke satt opp enda.
 gnome-colors krever gnome-dust-icon-theme. Men:
  Pakke gnome-dust-icon-theme er ikke satt opp enda.
 gnome-colors krever gnome-human-icon-theme. Men:
  Pakke gnome-human-icon-theme er ikke satt opp enda.
 gnome-colors krever gnome-illustrious-icon-theme. Men:
  Pakke gnome-illustrious-icon-theme er ikke satt opp enda.
 gnome-colors krever gnome-noble-icon-theme. Men:
  Pakke gnome-noble-icon-theme er ikke satt opp enda.
 gnome-colors krever gnome-wine-icon-theme. Men:
  Pakke gnome-wine-icon-theme er ikke satt opp enda.
 gnome-colors krever gnome-wise-icon-theme. Men:
  Pakke gnome-wise-icon-theme er ikke satt opp enda.
dpkg: Feil ved behandling av gnome-colors (--configure):
 kravproblem - setter ikke opp pakken
Setter opp opera (11.01.1190) ...
update-alternatives: error: cannot stat /lib/plymouth/themes/initrd.img-2.6.35-25-generic-pae/initrd.img-2.6: Ikke en filkatalog
dpkg: Feil ved behandling av opera (--configure):
 underprosessen installerte post-installation skript returnerte feilstatus 2
Ingen apport-rapport skrevet for MaxReports allerede er nådd
                                                            Det oppsto feil ved behandling av:
 gnome-colors-common
 gnome-brave-icon-theme
 gnome-dust-icon-theme
 gnome-human-icon-theme
 gnome-illustrious-icon-theme
 gnome-noble-icon-theme
 gnome-wine-icon-theme
 gnome-wise-icon-theme
 gnome-colors
 opera
E: Sub-process /usr/bin/dpkg returned an error code (1)
linux@ubuntu:~$ 

``` :confused: I got this problem by installing the Opera 11.01 .deb and all the Gnome icon packs from Software Cente. Ver. 10.10

---

### Post by gmargo on 2011-02-04
No offense to your language (only to my limited capacity), but could you run that again in english?

This will probably suffice:
```

$ sudo env LANG=C LC_ALL=C apt-get upgrade

```
(not sure about the LANG part)

---

### Post by SkyHookers on 2011-02-04
Umm... sorry for that. Im norwegian. and Ubuntu got automaticly to nb-NO.

Heres English Version:
```
linux @ ubuntu: ~ $ sudo apt-get upgrade 
[Sudo] password for linux: 
Reading package lists ... Done 
Building dependency ratio 
Reading state information ... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
10 packages not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y / n]? y 
Setting up gnome-colors-common (5.5.1-1) ... 
update-alternatives: error: can not state / lib/plymouth/themes/initrd.img-2.6.35-25-generic-pae/initrd.img-2.6: Not a directory 
dpkg: error processing gnome-colors-common (- configure): 
 during the process installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of gnome-brave-icon-theme: 
 gnome-brave-icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured yet. 
dpkg: error processing gnome-brave-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-jerk-icon-theme: 
 gnome-jerk-icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured yet. 
dpkg: error processing gnome-jerk-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-human-icon-theme: 
 gnome-human-icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured yet. 
dpkg: error processing gnome-human-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-illustrious-icon-theme: 
 gnome-illustrious-icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured enda.Ingen Apport report written because the error message indicates that it is due to error from a previous error. 
                                                                          No Apport report written because the error message indicates that it is due to error from a previous error. 
                  No Apport report written for MaxReports already reached 
                                                                              No Apport report written for MaxReports already reached 
                                                          No Apport report written for MaxReports already reached 
                                      No Apport report written for MaxReports already reached 
                  No Apport report written for MaxReports already reached 
                                                                              No Apport report written for MaxReports already reached 

dpkg: error processing gnome-illustrious-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-noble-icon-theme: 
 gnome-noble-icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured yet. 
dpkg: error processing gnome-noble-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-wine-icon-theme: 
 gnome-wine-icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured yet. 
dpkg: error processing gnome-wine-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-GroupWise icon-theme: 
 gnome-GroupWise icon-theme requires gnome-common-colors. But: 
  Package gnome-colors-common is not configured yet. 
dpkg: error processing gnome-wise-icon-theme (- configure): 
 dependency problems - leaving unconfigured Package 
dpkg: dependency problems prevent configuration of gnome-colors: 
 gnome-colors requires gnome-brave-icon-theme. But: 
  Package gnome-brave-icon-theme is not set up yet. 
 gnome-colors requires gnome-jerk-icon-theme. But: 
  Package gnome-jerk-icon-theme is not set up yet. 
 gnome-colors requires gnome-human-icon-theme. But: 
  Package gnome-human-icon-theme is not set up yet. 
 gnome-colors requires gnome-illustrious-icon-theme. But: 
  Package gnome-illustrious-icon-theme is not set up yet. 
 gnome-colors requires gnome-noble-icon-theme. But: 
  Package gnome-noble-icon-theme is not set up yet. 
 gnome-colors requires gnome-wine-icon-theme. But: 
  Package gnome-wine-icon-theme is not set up yet. 
 gnome-colors require gnome-icon-wise-theme. But: 
  Package gnome-GroupWise icon-theme is not set up yet. 
dpkg: error processing gnome-colors (- configure): 
 dependency problems - leaving unconfigured Package 
Setting up opera (1/11/1190) ... 
update-alternatives: error: can not state / lib/plymouth/themes/initrd.img-2.6.35-25-generic-pae/initrd.img-2.6: Not a directory 
dpkg: error processing opera (- configure): 
 during the process installed post-installation script returned error exit status 2 
No Apport report written for MaxReports already reached 
                                                            Errors were encountered while processing: 
 gnome-colors-common 
 gnome-brave-icon-theme 
 gnome-jerk-icon-theme 
 gnome-human-icon-theme 
 gnome-illustrious-icon-theme 
 gnome-noble-icon-theme 
 gnome-wine-icon-theme 
 gnome-GroupWise icon-theme 
 gnome-colors 
 opera 
E: Sub-process / usr / bin / dpkg Returned an error code (1) 
linux @ ubuntu: ~ $ 
```
Created By Using Google Translator.

---

