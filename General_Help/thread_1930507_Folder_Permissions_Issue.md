---
title: "Folder Permissions Issue"
date: 2012-02-23
forum: General Help
---

### Post by uRock on 2012-02-23
I am trying to create a new VBox, but I am getting the error in the screenshot. Here are the folder permissions via the ls command.```
urock@uRock-Desktop:~$ chown -R urock:urock VirtualBox\ VMs/
urock@uRock-Desktop:~$ ls -ail Virtual*
total 20
7341382 drwxrwxrwx  5 urock urock 4096 2012-02-10 14:10 .
7340033 drwxr-xr-x 53 urock urock 4096 2012-02-22 20:14 ..
7341401 drwxrwxr-x  3 urock urock 4096 2012-02-21 20:37 lubuntu
7341392 drwxrwxr-x  3 urock urock 4096 2012-02-22 16:28 ubuntu 10.04
7341383 drwxrwxr-x  3 urock urock 4096 2012-02-21 20:39 Ubuntu 10.10

7341382 drwxrwxrwx  5 urock urock 4096 2012-02-10 14:10 VirtualBox VMs
```What do I need to do in order to be able to get this working?

---

### Post by Dark Psycho on 2012-02-23
try this out: ```
sudo virtualbox
```

---

### Post by efflandt on 2012-02-23
I don't know much about VirtualBox, so I could be off base. But what does ownership of what I assume is "/home/urock/VirtualBox VMS" have to do with the error about "/home/rabbit/VirtualBox VMS"?

---

### Post by uRock on 2012-02-23
Running as root won't fix the folder permissions.

---

### Post by uRock on 2012-02-23
> **efflandt said:**
> I don't know much about VirtualBox, so I could be off base. But what does ownership of what I assume is "/home/urock/VirtualBox VMS" have to do with the error about "/home/rabbit/VirtualBox VMS"?

Thanks for sarcastically pointing out the problem. I have fixed the problem.

---

