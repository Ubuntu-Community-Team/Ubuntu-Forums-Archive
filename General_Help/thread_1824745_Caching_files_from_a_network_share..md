---
title: "Caching files from a network share."
date: 2011-08-14
forum: General Help
---

### Post by NomadicExistance on 2011-08-14
Hi All, I'm a complete newbie to Ubuntu/Linux... I've just installed 11.04 on my laptop - no dual boot, no Windows. I have a Linkstation Live 2TB NAS device on which I store all my music. I'm looking for a way to use the music by making the shared folder available when I'm not connected to my home network. Is there anyway I can do this (without actually making a local copy of all the files)... With Windows, I had the option of mapping the shared folder and making it available offline. I have tried looking at rsync, but is too complicated for my limited Linux knowledge. 

Please advise... :confused:

---

### Post by Hugh971 on 2011-08-14
Hi, looks like you're on the right track with rsync.

It's not too bad once you get used to it. Try running

```
rsync -r /path/to/network/music /local/synced/path
```

That will copy all the stuff from the music source to the destination and then when you run it again it should only copy modified or new files.

---

### Post by HereInOz on 2011-08-14
To my knowledge, no.  Happy to be corrected, though.  Oddly, all the Windows "make available offline" does is create a background synced copy on your local machine anyway, so it really is making a local copy.

With a tiny bit of effort, you could learn how to write a 3 line script which invokes rsync and that will sync any changes to your music store.  It isn't hard.  I avoided rsync for years, then finally wrote a backup script and have been using it ever since.

The trickiest bit is going to be mounting the Samba share, using the script, so it can access the NAS device, which is probably using Windows SMB networking. 

A script something like:

#!/bin/bash

mount -t smbfs -o username=yourusername,password=yourpassword //IP_address_of_the_NAS_device/music_folder /mnt/music

rsync -av /mnt/music /location_of_your_local_music/music

umount //IP_address_of_the_NAS_device/music_folder

ought to do it.

The mount location is entirely up to you, I used /mnt/music purely for illustration.  Just make sure that the mount folder exists first, before you try to mount the share in there.

You may have to install smbfs as well, if it is not already done.

---

### Post by NomadicExistance on 2011-08-14
Thanks Hugh. Just tried that and it threw an error. 
Command used... 

rsyc -r /*nas_device_name*/*media_folder_name*/music /home/*my_user*/MediaMount

Where MediaMount is what I'm tryng to sync my music to. 
The error was... 

rsync: change_dir "/*nas_device_name*/*media_folder_name*/music" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

Where am I going wrong?

---

### Post by NomadicExistance on 2011-08-14
Am gust going to try this again. I didn't have the music folder mounted. Maybe that's why the "No such file or directory"...:)

---

### Post by NomadicExistance on 2011-08-14
Is working. Thanks, the both of you! :)

---

