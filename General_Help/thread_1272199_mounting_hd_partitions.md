---
title: "mounting hd partitions"
date: 2009-09-21
forum: General Help
---

### Post by hockeyhead019 on 2009-09-21
hey guys,

ok well my title might be a little misleading... my hd partition mounts just fine but what i want to know is how can i have it automatically mount so that i can play the music out of it and have it be my "music library" so that when i add a song it auto updates...

i wanna figure this out because i have a ton of music and i dual boot windows and ubuntu and wish to be able to play music regardless of the os i'm runnin... so any help would be great...

thanks,
-Jim

---

### Post by Warren Watts on 2009-09-21
If you want to mount partitions automatically at boot, you just need to put them in /etc/fstab.

Here's a link that may help: [Automatically mounting partitions at boot]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing%20Ubuntu%27s%20filesystem%20table")

---

### Post by hockeyhead019 on 2009-09-21
ok great... and i assume that this will take care of the media library detection?

---

### Post by Warren Watts on 2009-09-21
> **hockeyhead019 said:**
> and i assume that this will take care of the media library detection?

Hmm..  Now **that** is an entirely different issue.  I would imagine that it would depend upon the media player being used to index and play the media???

---

### Post by hockeyhead019 on 2009-09-21
ok because that's what i'm really interested in haha... like i said i want to have my media library in the partition which i need to mount in order to gain access from both ubuntu and windows without needing to actually copy all the media files. so i'll try what you suggested and then see if i can't link my media library through that mounted partition. and i'm still looking for a good media player so i'll try them all out and see which one works if any for my requirements.

---

