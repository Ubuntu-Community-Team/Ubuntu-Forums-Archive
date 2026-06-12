---
title: "rsync acting weird"
date: 2009-12-28
forum: General Help
---

### Post by duffed on 2009-12-28
Hi,
 
I have setup a bash file with this rsync script into:
 
#!/bin/bash
rsync -vrat --delete --log-file=/home/duffed/RSyncLog/$(date +%Y%m%d)_rsync_Multimedia.log /media/Multimedia/ /media/MultimediaBackUp/
 
The script is run with cron and work #1. My only issues is rsync....
 
Base on my script rsync should add into the drive /media/MultimediaBackUp/ any files and folders located into /media/Multimedia/ ..... for some reason after a few run on my script, when I open the drive /media/MultimediaBackUp/ I have all the files and folder from /media/Multimedia/ thats fine, but I also have into /media/MultimediaBackUp/ a folder name Multimedia and this folder also include all files from /media/Multimedia/ ... I don't know why.
 
Does anyone can help me? did I put someting wrong in my script?
 
Thanks
 
Seb

---

