---
title: "gEdit won't save on mounted network drive (cifs)"
date: 2010-06-28
forum: General Help
---

### Post by nexus0123 on 2010-06-28
Hi,

I'm pretty new to Linux and I'm having trouble with gEdit in Ubuntu 10.04. I have a line in the fstab file which automatically mounts a network drive every time I start up Ubuntu. I browse to a text file on the network drive and open it using gEdit and make changes to it. Then, when I hit the save button, a bright red warning appears:

[B]Could not save the file [path here]
gedit cannot handle file: locations in write mode. Please check that you typed the location correctly and try again.[/B]

This also happens if I do save as.

Then, after this error appears, the file actually disappears (gets deleted) from the network drive and in order to save it, I have to select save as again and type in the original filename.

The line in my fstab file is:

[B]//files.example.com/username  /media/Network-Drive  cifs  uid=myname,umask=000,credentials=[cred file here],domain=mydomain  0  0
[/B]
I'm not sure if this has something to do with the file permissions or gEdit itself or using cifs to mount. When I use the "ls -l" command on the file, I get

**-rwxr-xr-x 1 myname root   7402 2010-06-28 01:14 textfile.do**

which should be fine since the user has all permissions. Any ideas?

Thanks!

---

### Post by dino99 on 2010-06-28
to be able to save a file when editing with a file editor like gedit, you need to use sudo to enable the rights

sudo gedit *myfile*

fstab is not easy to tweak without error, so better to install and use a nice tool to do this stuff and more: mountmanager (set your prefs into: system admin mountmanager)

---

### Post by kellemes on 2010-06-28
This works for me with cifs..
```
//location   /mnt/location    cifs user, uid=1000, iocharset=utf8, rw, suid, credentials=/file.txt  0  0  
```

---

### Post by nexus0123 on 2010-06-29
dino99: I've tried using sudo gedit to open the file. I was shocked to find that even as root, it didn't allow me to save on the mounted network drive. I've tried the "Connect to server..." option in the places menu in Ubuntu to do the network mount, but I will try mountmanager.

kellemes: I tried all the additional options you suggested and in different combinations. None of them seemed to work.

I think the main problem has to do with permissions on the server. It's odd but the mount has permissions "**-rwxr-xr-x" **when I do an "ls -l" in the mount directory, which seems to suggest some missing write permissions (rw option didn't fix that).

Any other suggestions would be much appreciated..

---

