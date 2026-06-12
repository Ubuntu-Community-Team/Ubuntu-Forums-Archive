---
title: "Backing up files over NFS"
date: 2006-05-19
forum: General Help
---

### Post by Arndt on 2006-05-19
My workstation does not run any backup system. There is also a server, which is regularly backed up in the proper way. My home directory on the server is mounted on a directory on my workstation, so I have direct access to it. There is a lot of room on the server.

Is there a program which eases the task of backing up those files of mine on the workstation which I want to keep? A solution I've used in the past is to use 'find' to obtain what files were changed or new since last time, ignore big files I didn't care much about, and then pack them up in a tar archive with a descriptive name and copy it to the server. Any automation of that would be welcome.

---

### Post by badrinarayan on 2006-05-19
There is a little utility precisely for this purpose. [Google for rsync]("http://www.google.com/search?q=rsync") - you will find a lot of tutorials on how to use it. Also look at the [man page]("http://rsync.samba.org/ftp/rsync/rsync.html").

It is usually as easy as
```
rsync -a source username@machine:/path/to/dir
```

---

