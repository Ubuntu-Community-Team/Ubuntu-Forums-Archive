---
title: "vhcs2 install problem"
date: 2009-10-01
forum: General Help
---

### Post by shred_eng on 2009-10-01
hi, ive been trying to install vhcs2 and have followed a tutorial and googled stuff but can never complete it without errors. 

this is what looks like an error before the installation even gets going:

Use of uninitialized value $cfg{"CMD_HOSTNAME"} in concatenation (.) or string at /var/www/vhcs2/engine/setup/vhcs2-setup line 87.


and this is the final errors after the installation finishes:

Use of uninitialized value $fgid in getgrnam at /var/www/vhcs2/engine/setup/vhcs2-setup line 797, <STDIN> line 8.
Use of uninitialized value $cfg{"CMD_GROUPADD"} in concatenation (.) or string at /var/www/vhcs2/engine/setup/vhcs2-setup line 801, <STDIN> line 8.
Use of uninitialized value $fgid in concatenation (.) or string at /var/www/vhcs2/engine/setup/vhcs2-setup line 801, <STDIN> line 8.
ERROR: External command ' ' returned '255' status !


if i had a clue what this is pointing to i might be able to fix it

this is on ubuntu server 904

any help appreciated , thx,

---

