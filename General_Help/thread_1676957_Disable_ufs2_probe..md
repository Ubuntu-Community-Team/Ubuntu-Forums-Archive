---
title: "Disable ufs2 probe."
date: 2011-01-28
forum: General Help
---

### Post by MythosLegend on 2011-01-28
Hi. I'm trying to disable linux from even being able to list ufs2 partitions as mountable. The ufs2 partitions do not automount but it still shows up as an icon in the places drop-down menu.
Palimpsest puts all 4 extended partitions of /dev/sda2 (ufs2) into my /dev/sda4 (ext4) with the same name "21 GB Filesystem". 

I'm thinking about adding 
<match key="volume.fstype" string="ufs"
<append key="volume.ignore" bool=true
or something like that to a file. I just don't know where to look. 

Can someone point me to the file that prevents hal or whatever from probing this filesystem?
udi? fdi?

---

