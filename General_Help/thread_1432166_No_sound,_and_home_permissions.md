---
title: "No sound, and home/ permissions"
date: 2010-03-17
forum: General Help
---

### Post by meigwil on 2010-03-17
Hi,

I've installed Karmic on my parents' lenovo n200.

All is well, but the sound does not now work. It worked when I first installed, but stopped soon after. I've spent quite a few hours trying to fix this.

Soon after installation I moved /home to a separate partition. I noticed now that permissions on the new /home are set to root for every user, and I read that pulseaudio will not work if permissions are not for the user. I'm sure that this is the problem.

I've already tried chowning the directories to user:user, but although I get no errors, nothing changes. 

I'm now stuck.

I checked the filesystem and /home is highlighted in green, which (I think) is an executable. The old home directories are still there, as /old_home. 

Can anyone help, or should I reinstall (or something)?

Thanks,

Mei

---

### Post by prodigy_ on 2010-03-17
There are many threads about fixing sound in 9.10. It's a widely discussed problem. Solutions vary from removing pulseaudio (and thus using pure ALSA) or editing some config files to abandoning ALSA in favor of OSS4.

So in this case you really should search the forums first.

---

### Post by rnerwein on 2010-03-17
hi
you said you chowned the directories, but what's about the files inside the directories. did you change
them too ?
do a ls -la inside of a user directory.
ciao

i just see that you say your /home is highlighted green -> thats means drwxrwxrwx -
that has nothing to do with your problem but change it to 755 ( chmod 755 /home )

---

### Post by oldfred on 2010-03-17
Are you getting .dmrc errors which is common after moving a /home. This also has the correct permission & ownership settings for /home.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by meigwil on 2010-03-18
Thanks for your replies.

ALL files inside home are owned by root:root and are set to 777.

For a quick test, I created a directory on the desktop. It was set to root:root and 777. Chowning a chmoding does nothing to change this. (I did use sudo, and no errors were reported)

I read somewhere (but can't find it again!) that root owns any partitions by default (or something). 

I'll keep looking and trying stuff out and let you know.

Mei

---

### Post by meigwil on 2010-03-18
Just a heads up: I booted into recovery mode to try and chown the directories (instructions [here]("http://www.psychocats.net/ubuntu/separatehome#troubleshooting")) but they're still root:root.

Mei

---

### Post by oldfred on 2010-03-18
The link I gave on dmrc errors also says that others must not be allowed to write into /home and gives the correct settings.

---

### Post by mcduck on 2010-03-18
> **meigwil said:**
> Thanks for your replies.

ALL files inside home are owned by root:root and are set to 777.

For a quick test, I created a directory on the desktop. It was set to root:root and 777. Chowning a chmoding does nothing to change this. (I did use sudo, and no errors were reported)

I read somewhere (but can't find it again!) that root owns any partitions by default (or something). 

I'll keep looking and trying stuff out and let you know.

Mei
Does the separate partition use some Linux filesystem (like Ext3 or ext4)? Not being able to change ownership/permissions even with "sudo" sounds like you are trying to use a FAT or NTFS partition (which is not going to work, as those filesystems aren't able to handle fle ownerships and permisisons as Linux uses them, and some of the files in user's home directories require certain permissions...)

---

### Post by meigwil on 2010-03-19
"Not being able to change ownership/permissions even with "sudo" sounds like you are trying to use a FAT or NTFS partition"

This is it. I formatted it as NTFS as I thought they would be going back to to Windows. I'll backup the files and reformat as ext3. I'll let you know how it goes. 

Thanks!

Mei

---

### Post by meigwil on 2010-03-22
I moved the files back to the main partition, and sound magically reappeared. Thanks to all who helped!

Mei

---

