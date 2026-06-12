---
title: "Playing Music Over a network"
date: 2006-01-29
forum: General Help
---

### Post by benjfield on 2006-01-29
I have serveral gbs of music in a samba share file on my windows computer. Does any1 no a way/ a program that will allow me to add the songs to a playlist on my linux machine without transferring the songs to the hard drive. Ne help wld be appreciated. Thanks.

---

### Post by eriefisher on 2006-01-29
Have a look at [http://videolan.org]("http://videolan.org")
I think this is what you are looking for.

eriefisher

---

### Post by IYY on 2006-02-01
My favorite way of doing this is to just mount the SMB share and access it as though it was on my harddrive.

Here's the command I use (it's in my /etc/init.d, can only be read by root):

```
mount -t smbfs -o username=myname,password=mypassword //computername/sharename /media/myfolder/
```

computername is the name of the machine on which the MP3 files are. Sharename is what that shared folder is called  (MP3, in my case). I created the /media/myfolder folder.

Then if I want to browse these files, I can do so through Konqueror or just cd /media/myfolder. Any music player can play them.

---

### Post by borisattva on 2006-03-04
in rhythmbox you cal also drag and drop your music folder from smb into rhythmbox and that will add the songs to the library.

---

