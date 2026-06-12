---
title: "Ubuntu 10.04 and Samba doesnt like utf8"
date: 2010-10-05
forum: General Help
---

### Post by ftornell on 2010-10-05
Hi, when trying to mount a windows share in fstab:

//192.168.0.10/MediaLibrary /media/MediaLibrary cifs credentials=/fredrik/.smbcredentials,iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0

I can browse the files but my swedish chars like ÅÄÖ is messed up.
I have tried iso8859, iso8859-1, iso8859-15 but no luck!

If I copy a folder from Windows to a Samba share it looks like it is correct from the Windows point-of-view. But when in linux and browsing to the folder it's not correct there either!

Might not be samba at all? Just a locale setting on the machine?

---

### Post by DarthScape on 2010-10-05
Unicode!!!

---

### Post by ftornell on 2010-10-05
and by unicode u mean codepage=unicode,unicode or codepage=cp850?

Tried them all and did a mount -a but same issues...

But if it is on a samba share on the local ubuntu server and I copy files from Windows into the share, it could not have ANYTHING with the fsdab (the goal in fstab is to mount a windows share into linux) 2 diffrent things

---

### Post by phylae on 2011-06-10
I'm sorry to resurrect an old thread, but I had a similar issue. I solved my problem by following the example in this thread: [http://ubuntuforums.org/showthread.php?t=1773700&highlight=samba+utf8](http://ubuntuforums.org/showthread.php?t=1773700&highlight=samba+utf8)

The key was adding iocharset=utf8 to the entry in /etc/fstab. After that I could view files encoded with utf8.

---

