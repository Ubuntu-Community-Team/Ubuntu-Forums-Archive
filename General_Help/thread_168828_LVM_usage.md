---
title: "LVM usage"
date: 2006-05-01
forum: General Help
---

### Post by ariek on 2006-05-01
Hi,
   
  Hopefully someone can answer my question about LVM. I am using 2 IDE harddisks at the moment, hda & hdb. hdb, with 1 partition only, is reaching it's capacity of 320 GB.
  Now I have added a new 120 GB harddisk, hdc.
  During the installation of my server I did not configure LVM. I do, however, would like to maintain 1 volume.
   
  I would like to achieve the following:
  1. "Convert" hdb (hdb1) to a LVM-volume;
  2. Add hdc to the converted volume.
   
  Can anyone please tell me if the above is possible? If not, are there other options to achieve this goal?
   
  I have read some of the LVM howto’s, but could not find the neccecairy information.
   
  Thanx for your reply.

---

### Post by duality on 2006-05-01
use EVMS, its much better and easier,, its well documented too.
[http://evms.sourceforge.net/user_guide/](http://evms.sourceforge.net/user_guide/)
Heres the guide

But its still verry complext so be carefull to not make misstakes.

you run it in ubuntu with "sudo evmsn"

gl

---

