---
title: "VMplayer not configured?"
date: 2006-06-05
forum: General Help
---

### Post by Jose Catre-Vandis on 2006-06-05
Using the install from the repos, I get and error status 1. This tells me to use the configuration tool that comes with vmplayer 

> /usr/bin/vmware-configure.pl

I do this and answer yes/no as required and then I get:

> VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

And we go round and round in circles. The thing seems to be compiling OK, but on initial install looked like it had problems with networking. Removing and reinstalling didn't help either?

---

### Post by Ramses de Norre on 2006-06-05
```
sudo /usr/bin/vmware-config.pl

``` worked for me.

---

### Post by Jose Catre-Vandis on 2006-06-05
[QUOTE=Ramses de Norre]```
sudo /usr/bin/vmware-config.pl

``` worked for me.[/QUOTE]

Sorry. I meant

>  /ur/bin/vmware-config.pl
(and not vmplayer-config.pl)

Will edit original post

---

