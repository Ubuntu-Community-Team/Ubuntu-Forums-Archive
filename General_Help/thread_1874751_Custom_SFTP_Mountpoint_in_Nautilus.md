---
title: "Custom SFTP Mountpoint in Nautilus"
date: 2011-11-03
forum: General Help
---

### Post by toseethefruit on 2011-11-03
Hello everyone,

I have a question that I've been researching for several days, for which I can't find an answer.

I'm running Ubuntu 11.04 with the Classic Gnome environment. I'm trying to figure out a way to set a custom mountpoint for an FTP server that I'm accessing. 

I know that I can use "File / Connect to Server..." in Nautilus and that the mount will then be made at /.gvfs. I need a custom mountpoint, though -- Mendeley, a reference manager that I'm trying to use, has a file manager within it that I need to use, and it can't see Ubuntu's hidden folders.

Does anyone know how I might accomplish this? Thank you very much for any help you might be willing to give!

My best,
J.

---

### Post by toseethefruit on 2011-11-07
Sorry, does anyone have any idea about this? I also tried sshfs, but it doesn't seem to be connecting. I would be very grateful for any pointers!

My best,
J.

---

### Post by Lars Noodén on 2011-11-07
> **toseethefruit said:**
>  I also tried sshfs, but it doesn't seem to be connecting.

Can you connect with the regular sftp client with the -v option?

---

### Post by crdlb on 2011-11-07
Can you drag-and-drop from the share in Nautilus to that application? I don't know if that's applicable to your situation, but it should work even without explicit GIO support.

---

### Post by toseethefruit on 2011-11-09
Lars and crdlb, thank you so very much for your suggestions. crdlb, I wasn't able to drag and drop into the program (it has a tree structure with checkboxes next to each folder), but, as it turns out, following Lars' reply actually led me to find another solution. I realized that I *was* able to connect to the server with the regular sftp client, so I knew that my connection settings were correct. I then went back and re-read all of the manual pages for sshfs and found that I had misunderstood how to set up an sshfs connection before. I needed to add a specific directory on the server that I wanted to mount to my local computer:

```
 sshfs [username]@ftp.servername.com:server-folder-name ~/local-folder-name
```

I hadn't been including the server-folder-name. Mea culpa.

I'm writing all of this down here in case anyone in the future has a similar problem. sshfs definitely seems like the best option for me to mount a server folder to a local folder, then, and is almost just as easy as using Nautilus' "Connect to Server" option. Again, thank you both!

My best,
J.

---

### Post by geoybest on 2012-06-24
I just encountered the same problem and found the answer in the following discussion thread:
[http://ubuntuforums.org/showthread.php?t=1474597]("http://ubuntuforums.org/showthread.php?t=1474597")

You may find the mount-points under ~/.gvfs/

> **toseethefruit said:**
> Hello everyone,

I have a question that I've been researching for several days, for which I can't find an answer.

I'm running Ubuntu 11.04 with the Classic Gnome environment. I'm trying to figure out a way to set a custom mountpoint for an FTP server that I'm accessing. 

I know that I can use "File / Connect to Server..." in Nautilus and that the mount will then be made at /.gvfs. I need a custom mountpoint, though -- Mendeley, a reference manager that I'm trying to use, has a file manager within it that I need to use, and it can't see Ubuntu's hidden folders.

Does anyone know how I might accomplish this? Thank you very much for any help you might be willing to give!

My best,
J.

---

### Post by bf65 on 2013-01-21
make a symbolic link to the .gvfs directory

/home/you> ln -s "/home/you/.gvfs/SFTPDIR" /home/you/visibledir

---

