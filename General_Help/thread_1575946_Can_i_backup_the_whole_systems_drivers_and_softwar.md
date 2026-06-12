---
title: "Can i backup the whole systems drivers and software, and install back later?"
date: 2010-09-16
forum: General Help
---

### Post by jhal114 on 2010-09-16
Hi,
Im very new to Ubuntu, but im enjoying myself from the new lucid.

i just wanted to ask, because i had sooo many times of system failure, which i had to 
reinstall all the time, can i backup the whole system, including all the software installed, and drivers, and fonts etc, to install back as is now?

everytime i mess up with the system, (because i learn by messing up :D ) 
i had to reinstall every single drivers, and fonts, language, and the UPDATE taking up soooo long......
so i just wanted to ask if there is any way i might burn the whole current system in a dvd or a usb?

thanks a lot for reading, please be kind to leave any answer if you know how... help the newbie! xD

---

### Post by lukeiamyourfather on 2010-09-16
Create an image of your disk and save it somewhere else. If you hose it, copy the image back to the disk. There's lots of commercial software out there for it, a few open source tools, and a few commands in Linux already on your machine for it. Search the forums and the Internet for cloning/imaging a disk in Linux.

---

### Post by jhal114 on 2010-09-16
Thanks a lot for the fast reply, and guiding me where should i start my search, because i really had no idea at all :)

heres what i found, would doing this restore where i am?

* Backing up

1. $ sudo su

2. $ cd /

3. $ tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/media --exclude=/sys /

4. 'tar: Error exit delayed from previous errors' (ignore)

5. backup.tgz (is in the root, copy this to a cd or a dvd)


* restore
1. backup.tgz (copy to the root folder)

2. $ sudo su

3. unzip
$ tar xvpzf backup.tgz -C /

4. make the directories back to where they were 
$ mkdir proc
$ mkdir lost+found
$ mkdir mnt
$ mkdir sys
$ mkdir media

---

### Post by Mark Phelps on 2010-09-16
HOW you do this is up to you, but with Clonezilla, you can easily backup and restore the entire system and/or individual partitions.

---

### Post by jhal114 on 2010-09-16
Thanks much for the help- much appreciated! :)

found out an open source program called remastersys- and just done a backup of my system.

i am not sure if it will create exact replica, but i do believe so :)

so that is solved now, thanks all for the help again!

---

