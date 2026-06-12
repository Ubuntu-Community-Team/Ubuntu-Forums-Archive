---
title: "merging two tomboy folders using grsync"
date: 2012-10-05
forum: General Help
---

### Post by dragonfly41 on 2012-10-05
What is the recommended way of manually merging two different tomboy folders.

i.e. rsync from one ubuntu 10.10 installation to another ubuntu 12.04 locally in different mounted partitions?

I tried Grsync session ..

[COLOR=Blue]*** Launching RSYNC command:
rsync -r -t -p -g -x -v --progress -s /home/dl/.local/share/tomboy/ /media/Ubuntu-12.04.1/home/dl/.local/share/tomboy/[/COLOR]

and this copied into the target tomboy folder .. but when opening tomboy in the target ubuntu the transferred (merged) files were not indexed by the tomboy GUI.

I tried Ubuntu One sync but that didn't work for some reason.  See screenshot.

---

### Post by dragonfly41 on 2012-10-05
Partly solved.  
I found that after the next boot of ubuntu-12.04 my merged tomboy folder was indexed correctly to show the uploaded (merged) tomboy notes

Meanwhile I found these ..

[http://askubuntu.com/questions/133322/tomboy-failed-to-sync-500-internal-server-error](http://askubuntu.com/questions/133322/tomboy-failed-to-sync-500-internal-server-error)

[https://bugs.launchpad.net/ubuntuone-servers/+bug/554313](https://bugs.launchpad.net/ubuntuone-servers/+bug/554313)

...

I'll have to explore further why Ubuntu One doesn't sync with tomboy.


[Later edit]

I found this reference which explains why Ubuntu One doesn't sync with tomboy.

[http://voices.canonical.com/ubuntuone/2012/02/05/an-important-note-about-notes/](http://voices.canonical.com/ubuntuone/2012/02/05/an-important-note-about-notes/)

One solution I've now read is - in tomboy preferences sync - to sync Tomboy with a _local_ folder and then rsync between these proxy folders in source and destination ubuntu.

rsync between tomboy folders directly is not recommended because of metadata.

---

