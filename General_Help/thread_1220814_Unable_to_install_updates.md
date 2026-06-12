---
title: "Unable to install updates"
date: 2009-07-23
forum: General Help
---

### Post by Oldhacker on 2009-07-23
This morning, the update arrow appeared and an error box said that the software index is broken. After following instructions to use Synaptic or sudo apt-get install -f (I tried both) I got the following:
brooks@brooks-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerracv
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 23.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 190807 files and directories currently installed.)
Removing cinelerracv ...
Description:	Ubuntu 8.10
de_DE.iso885915
es_ES.iso885915
fr_FR.iso885915
it_IT.iso885915
pt_BR.iso885915
sl_SI.iso885915
eu_ES.iso885915
eu_FR.iso885915
en_US.iso885915
locale "ru_RU.KOI8-R" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerracv (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)
brooks@brooks-desktop:~$ whereis cinelerracv
cinelerracv:
brooks@brooks-desktop:~$

---

### Post by Oldhacker on 2009-07-23
Since posting, I did some more analysis on my own.
The thing that was hanging update was a broken package of Cinelerracv. I couldn't uninstall it because it was not fully installed. If memory serves, I interrupted the original install because it wanted to put a link to my desktop. Therefore, I re-installed the whole package from synaptic Package Manager. My error messages went away, and I was able to install today's normal updates. :-)

---

