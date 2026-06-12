---
title: "Access Mounted SFTP Folder from Within Programs"
date: 2011-03-08
forum: General Help
---

### Post by andypi on 2011-03-08
I have a project stored on a university server which I'd like to be able to work on from home.

I already have an SFTP folder set up, which I can access easily in Nautilus, and I can freely copy files back and forth, or open them in e.g. gedit.

However, the project is in Matlab, and I cannot see the mounted SFTP folder from within Matlab. This means that I can't work on the project in Matlab without copying the whole lot across to my local machine when I want to work on it.

Is there some way I can get Matlab to "see" the connection so that I can use the mounted SFTP folder like any other in my filesystem? It appears on my desktop when connected - does it have some other mount location?

Thanks

---

### Post by blueridgedog on 2011-03-08
How are you mounting the sftp location now?  You should be able to mount it to a location in your filesystem then access it normally:

```
mkdir ~/UniversityFiles
sshfs HOSTuser@remote.host.or.ip:/host/dir/to/mount ~/UniversityFiles
```

Then open your program and go to the mounted location.

---

### Post by andypi on 2011-03-08
Thanks. Presumably I wasn't actually mounting the folder before. It was just a Nautilus launcher. I had assumed that it was actually mounted because when I right click on it after the connection is opened, one of the menu options is "unmount".

Anyway, now working fine. Thanks.

---

