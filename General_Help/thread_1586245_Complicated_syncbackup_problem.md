---
title: "Complicated sync/backup problem"
date: 2010-10-01
forum: General Help
---

### Post by SpinningAround on 2010-10-01
My parents have a photo album that I to some extent maintain, since don't live in there proximity, will I try to setup a backup server (OpenSSH/ssh/sftp). The though is to have a server where new images is uploaded, that then can be used to sync backups of the album. I would also like to be able to remove unwanted images on my version of the album that is then removed from the backup and also from my parents computer. Problem is that they usually don't remove these images from the camera which will cause these unwanted images to be re-added together with new photos.

Thought is that it should go something like this. 
Parents upload new images to there computer
These are uploaded to the backup server
I get the new photos when I sync with the server
I remove a few images
These images are then removed from the server
and from my parents computer
(// tricky part)
New photos are added to my parents computer and with them old deleted once
They sync with the server that notice that unwanted images are percent and therefore wont upload these images (and) delete these from my parents photo album.

I'm thinking about some kind of log file to keep track on which files that should not be uploaded. A bonus would be if it was possible to get some kind of notification if images have been added that are not in the 'delete file' but are older then the most recent backup.

I'm not sure if there exist a perfect solution for my problem, so I guess some scripting/programming will be required. Question is where to start.

---

