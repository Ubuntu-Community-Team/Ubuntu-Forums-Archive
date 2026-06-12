---
title: "smb path in terminal"
date: 2006-05-23
forum: General Help
---

### Post by dyarza on 2006-05-23
Is there a way to navigate to an smb path in a terminal?  I can't seem to get to anything.

Sorry for the remedial question, it has been a while since I have used Linux.  OSX has me spoiled.

Thanks,

David

---

### Post by unnes on 2006-05-23
Suppose I have a folder called "movies" shared on a computer with a WAN IP address of 192.168.2.4.

I would mount the folder as a local drive as follows:

```
sudo mkdir /media/movies
sudo mount //192.168.2.4/movies /media/movies/
```

Hopefully this answers your question. Provided you have the appropriate permissions to read/write/execute, you should be able to navigate the shared folder as normal mounted drive.

---

