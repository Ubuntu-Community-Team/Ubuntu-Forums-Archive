---
title: "SMB mount locking up"
date: 2006-01-22
forum: General Help
---

### Post by borisattva on 2006-01-22
up untill now ive always used smb://etc to play my music on the NAS through Rhythmbox, then i found EasyTag which does not support it so i had to mount the music library to /mnt/music. It was successfull and i was able to do the tagging magic with ease.

thats until i tried to simultaneously play the library as i was tagging it.

even though it wasnt handling the same same file or even the same folder, after a few moment of playing my EasyTag locked up. rhythmbox continued playing so i thought EasyTag was just ADD'ing on me and let it do its thing, untill Rhythmbox locked up as well, followed by the Nautilus instance i had open that was displaying the mounted folder.

i force closed everything and made rhythmbox play the libarry through the now mounted drive and not via smb://. it played untill i loaded easytag which again worked for a little as rhythmbox last time and then locked up.

is this some sort of a smb limitation in multitasking mount access, or is there a setting i need to tweak somewhere?

---

### Post by borisattva on 2006-01-23
further playing with this i discovered something else which i think could be the real source of the problem.

i have the same network drive available via mounted /mnt/shared driver and via network neighbourhood.

via network, all file names are displayed as they are in actuality, but

when viewing them via the mounted folder, accented characters are missing their accents. all such 'converted' files are inaccessible. probably because the file system looks for them under those false names when in the network source they are still accented.

is there some kind of a parameter i have to specify in my fstab to ensure that the network drive is mounted with full character support?

---

