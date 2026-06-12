---
title: "timidity failure"
date: 2011-03-14
forum: General Help
---

### Post by kooley on 2011-03-14
hello, im having a bit of a problem every time i try and install something either via shell or synaptic i get an error saying something about timidity failing or something. for example this is the error when i try and install a program in the shell 

"Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

can anyone tell me how to fix this? and what it means?

thank you

---

### Post by mastablasta on 2011-03-14
have you checked the software sources? 
perhaps it might be a good idea to upgrade your Ubuntu version. though 8.04 should be supported until april this year.

---

### Post by ajgreeny on 2011-03-14
I suspect you have a broken package.  Try ```
sudo apt-get install -f
```which may fix the broken timidity package for you.  If that is not successful use synaptic and go to **edit ->fix broken packages** which can sometimes work when the comand line does not, for somw weird reason.

If you need to reinstall it, it is probably worth removing the packages for timidity that are in **/var/cache/apt/archives** just in case they are corrupt

---

